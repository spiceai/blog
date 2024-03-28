---
date: 2024-03-28
title: 'Adding Spice - The Next Generation of Spice.ai OSS'
type: blog
linkTitle: 'Adding Spice'
author: Phillip LeBlanc ([@phillipleblanc](https://twitter.com/phillipleblanc))
categories: [spiceai]
tags: [spiceai, data, infra, oss, rust]
---

**TL;DR:** We rebuilt [Spice.ai OSS](https://github.com/spiceai/spiceai) from the ground up in Rust, as a unified SQL query interface and portable runtime to locally materialize, accelerate, and query data tables sourced from any database, data warehouse or data lake. Learn more at [github.com/spiceai/spiceai](https://github.com/spiceai/spiceai).

In September, 2021, we [introduced](https://blog.spiceai.org/posts/2021/09/07/introducing-spice.ai-open-source-time-series-ai-for-developers/) Spice.ai OSS as a runtime for building AI-driven applications using time-series data.

We quickly ran into a big problems in making these applications work... data, the fuel for intelligent software, was painfully difficult to access, operationalize, and use, not only in machine learning, but also in web frontends, backend applications, dashboards, data pipelines, and notebooks. And we had to make hard tradeoffs between cost and query performance.

We felt this pain every day building 100TB+ scale data and AI systems for the [Spice.ai Cloud Platform](https://spice.ai/). So we took our learnings and infused them back into Spice.ai OSS with the capabilities we wished we had.

We rebuilt Spice.ai OSS from the ground up in Rust, as a unified SQL query interface and portable runtime to locally materialize, accelerate, and query data tables sourced from any database, data warehouse or data lake.

<div style="display: flex; justify-content: center; padding: 5px;">
  <div style="display: grid;">
    <img style="max-width: 900px; margin: auto" alt="OGP" src="https://github.com/spiceai/spiceai/assets/80174/f71f227d-d7cd-418c-85b9-5c663a728491">
    	<div style="font-size: 0.8rem; font-style: italic; text-align: center;">Figure 1. Spice.ai OSS</div>
  </div>
</div>

Spice is a fast, lightweight (< 150Mb), single-binary, designed to be deployed alongside your application, dashboard, and within your data or machine learning pipelines. Spice federates SQL query across databases (MySQL, PostgreSQL, etc.), data warehouses (Snowflake, BigQuery, etc.) and data lakes (S3, MinIO, Databricks, etc.) so you can easily use and combine data wherever it lives. Datasets, declaratively defined, can be materialized and accelerated using your engine of choice, including DuckDB, SQLite, PostgreSQL, and in-memory Apache Arrow records, for ultra-fast, low-latency query. Accelerated engines run in your infrastructure giving you flexibility and control over price and performance.

### Before Spice

<div style="display: flex; justify-content: center; padding: 5px;">
  <div style="display: grid;">
    <img style="max-width: 750px; margin: auto" alt="Before Spice" src="https://github.com/spiceai/spiceai/assets/80174/0550d682-cf3b-4b1b-a3bd-d8b3ad7d8caf">
    	<div style="font-size: 0.8rem; font-style: italic; text-align: center;">Figure 2. Before Spice, applications submit many queries to external data sources.</div>
  </div>
</div>

### With Spice

<div style="display: flex; justify-content: center; padding: 5px;">
  <div style="display: grid;">
    <img style="max-width: 900px; margin: auto" alt="After Spice" src="https://github.com/spiceai/spiceai/assets/80174/b57514fe-d53d-42de-b8f0-97ae313c5708">
    	<div style="font-size: 0.8rem; font-style: italic; text-align: center;">Figure 3. With Spice, data is materialized and accelerated locally for fast, low-latency query.</div>
  </div>
</div>

### Use-Cases

The next-generation of Spice.ai OSS enables:

**Better applications.** Accelerate and co-locate data with frontend and backend applications, for high concurrent queries, serving more users with faster page loads and data updates. [Try the CQRS sample app](https://github.com/spiceai/samples/tree/trunk/acceleration#local-materialization-and-acceleration-cqrs-sample).

**Snappy dashboards, analytics, and BI.** Faster, more responsive dashboards without massive compute costs. Spice supports Arrow Flight SQL (JDBC/ODBC/ADBC) for connectivity with Tableau, Looker, PowerBI, and more. [Watch the Apache Superset with Spice demo.](https://github.com/spiceai/samples/blob/trunk/sales-bi/README.md)

**Faster data pipelines, machine learning training and inference.** Co-locate datasets with pipelines where the data is needed to minimize data-movement and improve query performance. [Predict hard drive failure with the SMART data demo.](https://github.com/spiceai/demos/tree/trunk/smart-demo#spiceai-smart-demo)

**Easily query many data sources.** Federated SQL query across databases, data warehouses, and data lakes using [Data Connectors](https://docs.spiceai.org/data-connectors).

### Community Built

Spice is open-source, Apache 2.0 licensed, and is built using industry-leading technologies including Apache DataFusion, Arrow, and Arrow Flight SQL. We're launching with several built-in [Data Connectors](https://docs.spiceai.org/data-connectors) and [Accelerators](https://docs.spiceai.org/data-accelerators) and Spice is extensible so more will be added in each release. If you're interested in contributing, we'd love to welcome you to the community!

### Getting Started

You can download and run Spice in less than 30 seconds by following the quickstart at [github.com/spiceai/spiceai](https://github.com/spiceai/spiceai#quickstart).

<div style="display: flex; justify-content: center; padding: 5px;">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/AZyrecVWnEs?si=xKvMcNKvxNi_c8de" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### Conclusion

Spice, rebuilt in Rust, introduces a unified SQL query interface, making it simpler and faster to build data-driven applications. The lightweight Spice runtime is easy to deploy and makes it possible to materialize and query data from any source quickly and cost-effectively. Applications can serve more users, dashboards and analytics can be snappier, and data and ML pipelines finish faster, without the heavy lifting of managing data.

For developers this translates to less time wrangling data and more time creating innovative applications and business value.

Check out and [star the project on GitHub](https://github.com/spiceai/spiceai)!

Thank you,

Phillip
