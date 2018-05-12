# Metrics

## Dashboards, Counter, Gauge

Monitoring is important

- know when things are down
- understand system / application behaviour
- capacity planning

Author of "Doing Math With Python"
Fedora Scientific Creator / Maintainer

`https://github.com/amitsaha/python-monitoring-talk`

Metric = measure / value of quantity at a given point of time

(Matplotlib showcase)

# Types

- Counter: metric will always increase over time
- Gauge: metric can go up or down arbitrily (usually floored and ceilinged)
- Histogram: tracks observations, different from a gauge in that you can do operations on this metric

# Demo

`from helpers.middleware import setup_metrics`
