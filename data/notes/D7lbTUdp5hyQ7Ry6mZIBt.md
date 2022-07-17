
---
id: zznn7su9abv01q61qk6mym1
title: ASAP Time Series Paper
desc: ''
updated: 1657530669543
created: 1657460809018
---


[ASAP: Automatic Smoothing for Attention Prioritization in Streaming Time Series Visualization](https://arxiv.org/abs/1703.00983v1)

# Situation
Much telemetry data has been generated from various systems. For some of it there are human operators,
looking at it in order to do detect anomalies quickly.

But trend shifts can be hidden by variance.

Idea:

Smooth variance between first differences
subject to kurtosis (4th moment) remaining the same.

Find window length that does this best, calculate online (if possible).


# Implementations

[[engineering.technologies.MacroBase]]

[[science.cs.languages.JavaScript]]




# Task


# Action


Solve efficiently above problem..



**Acts as a transformation on fixed-size sliding windows and
over a single time series**


**ASAP can also execute on
the client; we provide a JavaScript library for doing so.**


***ASAP acts as a building block in time series visualization. It
can ingest and process raw data from time series databases such
as InfluxDB, as well as from visualization clients such as plotting
libraries and frontends**



## Roughness measure
it's the roughness of the **trend** (roughly).

Roughness = 0 <=> straight line .

## Preservation Measure

Kurtosis:

(4th standartised moment).
### Smoothing Function

It's just the simple moving average.

### Smoothing problem statement





# Result




