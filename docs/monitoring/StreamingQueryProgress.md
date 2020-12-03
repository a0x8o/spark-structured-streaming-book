# StreamingQueryProgress

`StreamingQueryProgress` is information about a single micro-batch (_progress_) of a [StreamingQuery](../StreamingQuery.md):

* <span id="id"> [Unique identifier](../StreamingQuery.md#id)
* <span id="runId"> [Unique identifier of a query execution](../StreamingQuery.md#runId)
* <span id="name"> [Name](../StreamingQuery.md#name)
* <span id="timestamp"> Time when a trigger has started (in ISO8601 format)
* <span id="batchId"> Unique ID of a micro-batch
* <span id="batchDuration"> Batch Duration
* <span id="durationMs"> Durations of the internal phases (in ms)
* <span id="eventTime"> Statistics of the event time as seen in a batch
* <span id="stateOperators"> [StateOperatorProgress](StateOperatorProgress.md) for every stateful operator
* <span id="sources"> [SourceProgress](SourceProgress.md) for every streaming source
* <span id="sink"> [SinkProgress](SinkProgress.md)
* <span id="observedMetrics"> Observed Metrics

`StreamingQueryProgress` is created when `StreamExecution` is requested to [finish a trigger](ProgressReporter.md#finishTrigger).

## Last and Recent Progresses

Use [lastProgress](../StreamingQuery.md#lastProgress) property of a `StreamingQuery` to access the most recent `StreamingQueryProgress` update.

```scala
val sq: StreamingQuery = ...
sq.lastProgress
```

Use [recentProgress](../StreamingQuery.md#recentProgress) property of a `StreamingQuery` to access the most recent `StreamingQueryProgress` updates.

```scala
val sq: StreamingQuery = ...
sq.recentProgress
```

## StreamingQueryListener

Use [StreamingQueryListener](StreamingQueryListener.md#QueryProgressEvent) to be notified about `StreamingQueryProgress` updates while a streaming query is executed.
