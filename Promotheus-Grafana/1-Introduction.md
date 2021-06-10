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

# Basic Concepts

all data is time series

every time series is identifiesd by a **metric name** and a set of **key-value pairs** called **labels**

    metric: go_memstat_alloc_bytes

time series data also consists of actual data called **samples**. It be either a **float64** value or a **millisecond-precision** timestamp.

The notation of time series id often this:

    <metric name>{<label name>=<label value>, ...}

## Prometheus Configuration

it is stored in `yaml` format.

we can change the config files and apply changes with having to restart Prometheus
> A reload can be done using `kill -SIGHUP <pid>`

we can also pass parameters at **startup time** to `./prometheus`
> these parameters cannot be changed without restarting Prometheus

The Configuration file is passed using `--config.file` flag

To scrape metrics, we need to add Configuration to the prometheus config file


## Architecture

see the Prometheus architecture diagram from Prometheus on GitHub.

## Monitoring Nodes

To monitor linux nodes, we need to install `node-exporter`. It exposed machine metrics like cpu usage, memory usage, etc. This is used to monitor machines, and later we can create alerts based on these ingested metrics.
> for windows we have a `WMI exporter`


# Prometheus Monitoring

* Client Libraries
* Pushing Metrics
* Querying using PromQL
* Service Discovery
* Exporters

## Client Libraries

Official libs available for Go, Java/Scaal, Python, Ruby
Unofficial libs are also available: Bash, C++

### Exposition formats:

* Simple text-based format
* Protobuf format - no longer supported after Prometheus 2.0

### Types of Metrics:

* Counter - simple value - only goes up
* Guage - a single numeric value that can go up & down
* Histogram - sample observations - counted in buckets
* Summary - samples observations

## Pushing Metrics

> Push gateway is used as an intermediary service which allows us to push metrics. This is generally helpful for servers not reachable due to firewall/NAT issues, batch jobs, etc.

It is a sinlge instance, so results in SPOF

Prometheus's automatic instance health monitoring is not possible. Be careful if you really need this. !!!

Push gateway never forgets the metrics unless deleted via API

## Querying

> provides a functional expression language called `PromQL`.

supports:

* built-in operations & functions
* vector based calculations like Excel
* Expressionss over time series vectors

PromQL is **read-only**

## Service Discovery

> is the automatic detection of devices and services offered by these devices on a computer network.

## Exporters

> exports lists of metrics

useful where code instrumentation is not possible.

We can see a list of available exporters [here][prometheus-exporters].

[prometheus-exporters]: https://www.prometheus.io/docs/instrumenting/exporters


# Alerting

We can rapidly identify problem causes and minimize surface degradation and disruption.
Metrics and other measurements facilitate observability and alerts draw human attention to the particular system that requires observation, inspection and intervention.

Alerting in Prometheus is separated into two parts.

* alerting rules - defined into The Prometheus server
* Alertmanager - routes, alerts to receivers, like pagerduty, Opsgenie, email, Slack, a custom wipebook.


You have a Prometheus server where the rules are defined, and then the alert got pushed to a route.
This route defines where the alert should go to, via the receivers.

> by default Alertmanager is not installed and you should alter the Prometheus configuration in `/etc/prometheus/prometheus.yml` in order to be able to reach the Alertmanager.

The Alertmanager runs on port 9093.
