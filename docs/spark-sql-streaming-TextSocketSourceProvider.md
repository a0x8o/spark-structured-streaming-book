# TextSocketSourceProvider

`TextSocketSourceProvider` is a [StreamSourceProvider](StreamSourceProvider.md) for [TextSocketSource](spark-sql-streaming-TextSocketSource.md) that read records from `host` and `port`.

`TextSocketSourceProvider` is also a `DataSourceRegister`.

The short name of the data source is `socket`.

It requires two mandatory options (that you can set using `option` method):

1. `host` which is the host name.
2. `port` which is the port number. It must be an integer.

`TextSocketSourceProvider` also supports <<includeTimestamp, includeTimestamp>> option that is a boolean flag that you can use to include timestamps in the schema.

=== [[includeTimestamp]] includeTimestamp Option

CAUTION: FIXME

=== [[createSource]] createSource

`createSource` grabs the two mandatory options -- `host` and `port` -- and returns an spark-sql-streaming-TextSocketSource.md[TextSocketSource].

=== [[sourceSchema]] sourceSchema

`sourceSchema` returns `textSocket` as the name of the source and the schema that can be one of the two available schemas:

1. `SCHEMA_REGULAR` (default) which is a schema with a single `value` field of String type.

2. `SCHEMA_TIMESTAMP` when `<<includeTimestamp, includeTimestamp>>` flag option is set. It is not, i.e. `false`, by default. The schema are `value` field of `StringType` type and `timestamp` field of spark-sql-DataType.md#TimestampType[TimestampType] type of format `yyyy-MM-dd HH:mm:ss`.

TIP: Read about spark-sql-schema.md[schema].

Internally, it starts by printing out the following WARN message to the logs:

```
WARN TextSocketSourceProvider: The socket source should not be used for production applications! It does not support recovery and stores state indefinitely.
```

It then checks whether `host` and `port` parameters are defined and if not it throws a `AnalysisException`:

```
Set a host to read from with option("host", ...).
```
