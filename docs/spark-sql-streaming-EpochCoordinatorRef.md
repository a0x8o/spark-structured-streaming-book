== [[EpochCoordinatorRef]] EpochCoordinatorRef

`EpochCoordinatorRef` is...FIXME

=== [[create]] Creating Remote Reference to EpochCoordinator RPC Endpoint -- `create` Factory Method

[source, scala]
----
create(
  writer: StreamWriter,
  reader: ContinuousReader,
  query: ContinuousExecution,
  epochCoordinatorId: String,
  startEpoch: Long,
  session: SparkSession,
  env: SparkEnv): RpcEndpointRef
----

`create`...FIXME

NOTE: `create` is used exclusively when `ContinuousExecution` is requested to <<ContinuousExecution.md#runContinuous, run a streaming query in continuous mode>>.

=== [[get]] Getting Remote Reference to EpochCoordinator RPC Endpoint -- `get` Factory Method

[source, scala]
----
get(id: String, env: SparkEnv): RpcEndpointRef
----

`get`...FIXME

[NOTE]
====
`get` is used when:

* `DataSourceV2ScanExec` leaf physical operator is requested for the input RDDs (and creates a <<spark-sql-streaming-ContinuousDataSourceRDD.md#, ContinuousDataSourceRDD>> for a <<spark-sql-streaming-ContinuousReader.md#, ContinuousReader>>)

* `ContinuousQueuedDataReader` is created (and initializes the <<spark-sql-streaming-ContinuousQueuedDataReader.md#epochCoordEndpoint, epochCoordEndpoint>>)

* `EpochMarkerGenerator` is created (and initializes the <<spark-sql-streaming-ContinuousQueuedDataReader-EpochMarkerGenerator.md#epochCoordEndpoint, epochCoordEndpoint>>)

* `ContinuousWriteRDD` is requested to <<spark-sql-streaming-ContinuousWriteRDD.md#compute, compute a partition>>

* `WriteToContinuousDataSourceExec` is requested to <<spark-sql-streaming-WriteToContinuousDataSourceExec.md#doExecute, execute and generate a recipe for a distributed computation (as an RDD[InternalRow])>>
====
