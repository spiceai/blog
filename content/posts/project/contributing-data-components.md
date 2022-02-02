---
date: 2022-02-01
title: "Adding a New Component to data-components-contrib"
type: blog
linkTitle: "Adding a New Component to data-components-contrib"
author: Phillip LeBlanc ([@leblancphill](https://twitter.com/leblancphill))
categories: [contributing, tutorial]
tags: [data-components-contrib, data connectors, data processors]
---

The `data-components-contrib` open source repository is the foundation on which the Spice.ai runtime ingests the data it needs. Data is crucial to any project that leverages ML. As discussed in a previous blog post, [AI needs AI-ready data](https://blog.spiceai.org/posts/2021/12/05/ai-needs-ai-ready-data/), the Spice.ai runtime handles the logistics of gathering the data and presenting it in an ML-ready format. The "gathering data" step is implemented through the logic of the data-components-contrib repo through data connectors and data processors.

The repository for the data-components-contrib is separate from the main `spiceai/spiceai` project because it is important to us to build these components with the community. The initial consumer of these data-components is the Spice.ai runtime - but any Golang-based project is able to take advantage of these data-components for their own use. By publishing the data-components as a separate project we are building a foundation that anyone can use and contribute to for their own needs.

In this post, we'll walk through adding a new data connector, integrate the new connector into a local version of Spice.ai and creating a Spicepod that uses our new data connector.

### Data Connectors and Data Processors

The data-components-contrib repo contains two types of components: **data connectors** and **data processors**.

A data connector is responsible for connecting to a data source, loading data from that data-source and passing the raw data onto the data processor. The user will indicate to the data connector through dataspace configuration what type of data to load and other configuration needed to connect to the data source. For the file connector this can be as simple as the path to the file, but for a database or datalake this could include the endpoint of the service to connect to as well as any connection strings or access keys required.

A data connector is also responsible for keeping track of what data it has sent through the pipeline and not re-sending data. For example, writing a data connector that connects to a database and runs SQL queries would need to either send queries that only return new data, or keep track of data already returned from a query and sending just the new data.

A data processor on the other hand, is responsible for taking the raw bytes that it receives from a data connector and processes them into an [Apache Arrow](https://arrow.apache.org/) record. We use Apache Arrow as our standard format for in-memory data for performance reasons - look out to a future blog post on why we chose this format and what benefits it offers. Once in the Apache Arrow format, the record is sent to the Spice.ai runtime.

[diagram of data flow from source, to data connector, to data processor, to runtime]

Data connectors and data processors can be mixed and matched as long as the data processor can understand the data from the data connector. So for example, if you use an HTTP data connector that gets data from an API and that API returns results in a JSON format, you could pass that payload to the JSON data processor and then the JSON processor would be able to convert that and pass it to the engine. But you can also have an HTTP API that returns CSV pass that to the CSV data processor.

### Tutorial

For this tutorial we will add a new data connector that watches a directory for new files and passes the content of those files to the data processor in the pipeline. When the connector starts up, it will read all of the files in the configured directory and pass all of the data along the pipeline, and then watch that directory for changes. Any modifications to existing files will resend the entire file. New files that appear in the directory will also be sent.

The first step is to clone the spiceai and data-components-contrib repositories. Once you have the projects cloned then let's run the build for each repository to ensure that we've got the dependencies set up correctly.

`spiceai` [point to CONTRIBUTING.md on how to install prerequisites, show running the Makefile to build the project]

`data-components-contrib` [run the tests to ensure that they have the pre-reqs]

The next step is set up the go modules so that your locally cloned Spice.ai points to your locally cloned data-components-contrib. We do this so that whenever you build Spice.ai it uses the code that you changed in data-components-contrib so you can reference a new data connector.

Here's the code to do that.

[show code snippet]

You can see you just need to use a go mod replace, and point it to your code local disk repository. Now let's create our new connector and we'll call it the directory connector. We'll need to edit the `dataconnector.go` file to indicate that there is a new data connector.

[show the dataconnector.go change]

We'll add a new directory.go file in a new `directory` folder under the dataconnectors. To implement a new connector, we'll need to implement this data connector interface.

[Show data connector interface]

[And here's a little explanation on the interface that we expose. blah blah blah]. You can see that it's optimized for a streaming scenario where your data can continuously be coming in. Let's imagine for our directory connector example that there's an external system that's continually writing new files to the directory and we want to be able to take whatever new file was written in the process and stream it to the Spice.ai runtime. This interface allows us the ability to do that.

Alright, so we have the interface now we need to start implementing it. Here's the code for the implementation the first step we'll need to do which is watch the directory for file changes.

[show code that will watch a directory for file changes]

On startup, we'll need to walk the directory and get the list of files to monitor. We'll keep a map in memory of the filename to a hash of the file contents. This allows us to know when we've seen a file already and skip it if the file system reports a change that doesn't actually change the contents of the file.

[code that walks directory on startup]

Now we can fill in our directory watcher to check this map and if its a file we haven't seen, or a file where the content has changed then we can read it and send it along. We also store in our map any new files that we are notified of.

Here's the code for this:

[code that fills in the directory watcher]

You'll notice that we haven't been worrying about the format of the files that we're reading. The data connector just cares about getting the data from the source and then passing it to a data processor. The data processor is responsible for parsing the files that we get here into the format that is needed. So if we're watching a directory that has CSV files, then we'd create a Spicepod that has a CSV data processor along with our new directory data connector.

Here's the we've got the final code for the for the directory data connector.

[final code file for directory.go]

Now let's go wire this up to Spice.ai and create a Spicepod that uses it.
