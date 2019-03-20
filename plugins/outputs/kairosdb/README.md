# KairosDB Output Plugin

This plugin writes [KairosDB](https://kairosdb.github.io/) using the telnet or http protocols.

KairosDB is a rewrite of OpenTSDB that uses Cassandra as a backend. However, there are several
differences between their http APIs to warrant a separate plugin. The opentsdb output does not
work with KairosDB. 

To use Http mode, use 'http://' in the host parameter. Otherwise, use 'tcp://'

See https://kairosdb.github.io/docs/build/html/restapi/AddDataPoints.html fir detauks.

### Configuration:

```toml
[[outputs.kairosdb]]
  ## TCP endpoint for writing to the KairosDB telnet interface
  # host = "tcp://kairosdb.example.com"
  # port = 4242

  ## HTTP endpoint for writing to the KairosDB REST API
  host = "http://lkairosdb.example.com"
  port = 8080

  ## Prefix metrics name
  prefix = "my.specific.prefix."

  ## Number of data points to send to KairosDB in Http requests.
  ## Not used with telnet API.
  http_batch_size = 50

  ## URI Path for Http requests to KairosDB.
  ## Used in cases where KairosDB is located behind a reverse proxy.
  http_path = "api/v1/datapoints"

  debug = true
  separator = "_"

  ## Number of data points to send to KairosDB in Http requests.
  ## Not used with telnet API.
  http_batch_size = 50

  ## Debug true - Prints KairosDB communication
  debug = false

  ## Separator separates measurement name from field
  separator = "_"
```
