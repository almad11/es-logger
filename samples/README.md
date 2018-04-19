Sample Configuration Files
==========================

## es-logger\_sample.conf

A sample logstash configuration to post Jenkins events generated by es-logger into
elasticsearch.

Key points to note:
* The mutate of the changeset date is because the output from the git build info data is not
  a date format parseable by elasticsearch.

## elasticsearch-template-es5x.json

A sample configuration for the elasticsearch template used in index generation.  The
differences from the default are:
* Addition of index.mapping.total\_fields.limit
    * Default of 1000 was being breached, so events were dropped.  Upping to 3000.

## /etc/kibana/kibana.yml

The kibana configuration was updated when index updates were receiving an error of
"Payload content length greater than maximum allowed: 1048576".

The following was added to the /etc/kibana/kibana.yml configuration file:
```
# The maximum payload size in bytes for incoming server requests.
server.maxPayloadBytes: 2097152
```