# Introduction

<blockquote>
Prometheus is an open source monitoring solution.
</blockquote>

In Prometheus we use dimensional data: time series are identifies by metric name and a set of key/value pairs also called as labels.

It includes a **query language**.

Visualizations can be shown using a built-n expression browser or with integrations like Grafana.

It stores metrics in memory and local disk in an own custom, efficient format.

It is written in Go.

Many client libraries and integrations available.

A single Prometheus server is able to ingest up to one million samples per second as several million time series.

### How does it work?

It scraps data from multiple HTTP endpoints.
