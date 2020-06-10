# Filter incoming data using nullqueues with regex

**$SPLUNK_HOME/etc/apps/search/local/props.conf**
```
[<spec>]
TRANSFORMS-null = some_data_filter_name
```
\<spec\> can be:
1. \<sourcetype\>, the source type of an event.
2. host::\<host\>, where \<host\> is the host, or host-matching pattern, for an
                 event.
3. source::\<source\>, where \<source\> is the source, or source-matching
                     pattern, for an event.
4. rule::\<rulename\>, where \<rulename\> is a unique name of a source type
                     classification rule.
5. delayedrule::\<rulename\>, where \<rulename\> is a unique name of a delayed
                            source type classification rule.
                            These are only considered as a last resort
                            before generating a new source type based on the
                            source seen.



If you want to filter based on multiple strings, you can do something like:

**$SPLUNK_HOME/etc/apps/search/local/transforms.conf**
```
[some_data_filter_name]
REGEX = (term1|term2|term\s3)
DEST_KEY = queue
FORMAT = nullQueue
```