---
date: 2022-02-01
title: "Adding a New Component to data-components-contrib"
type: blog
linkTitle: "Adding a New Component to data-components-contrib"
author: Phillip LeBlanc ([@leblancphill](https://twitter.com/leblancphill))
categories: [contributing, tutorial]
tags: [data-components-contrib, data connectors, data processors]
---

Spice.ai's vision for [more intro here]

In this tutorial, we'll walk through adding a data connector that connects to [blah], integrating it into a local version of Spice.ai and creating a Spicepod that uses our new data connector.

### Why data-components-contrib?

Data is crucial to any project that leverages ML. As discussed in a previous blog post, [AI needs AI-ready data](https://blog.spiceai.org/posts/2021/12/05/ai-needs-ai-ready-data/), the Spice.ai runtime handles the logistics of gathering the data and presenting it in an ML-ready format. The "gathering data" step is implemented through the logic of the data-components-contrib repo through data connectors and data processors.

The repository for the data-components-contrib is separate from the main `spiceai/spiceai` project because we felt it was important to build these components with the community. The initial consumer of these data-components is the Spice.ai runtime - but any Golang-based project is able to take advantage of these data-components for their own use.

### Data Connectors and Data Processors

The data-components-contrib repo contains two types of components: **data connectors** and **data processors**.

A data connector is responsible for connecting to a data source, loading data from that data-source and passing the raw data onto the data processor. The user will indicate to the data connector through dataspace configuration what type of data to load and other configuration needed to connect to the data source. For the file connector this can be as simple as the path to the file, but for a database or datalake this could include the endpoint of the service to connect to as well as any connection strings or access keys required.

A data connector is also responsible for keeping track of what data it has sent through the pipeline and not re-sending data. For example, writing a data connector that connects to a database and runs SQL queries would need to either send queries that only return new data, or keep track of data already returned from a query and sending just the new data.

A data processor on the other hand, is responsible for taking the raw bytes that it receives from a data connector and processes them into an [Apache Arrow](https://arrow.apache.org/) record. We use Apache Arrow as our standard format for in-memory data for performance reasons - look out to a future blog post on why we chose this format and what benefits it offers. Once in the Apache Arrow format, the record is sent to the Spice.ai runtime.

[diagram of data flow from source, to data connector, to data processor, to runtime]

### Tutorial

For this tutorial we will add a new data connector that connects to a [blah]
