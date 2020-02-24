# nifi-templates
Here you can find Apache Nifi templates. You're free to use, comments and suggestions for enhancement are appreciated.

1. Nifi rest authentication - /authentication
   Reusable process group authenticating using REST API. PG returns "Authorization" attribute with token. 
   It can be used in other rest api requests.
   
   Required actions before starting:
   - modify nifi.rest.* parameters
   - configure NifiSSLContextService (provide keystore, truststore paths and passwords)
   
2. Monitoring process groups : bulletins and drop events - /monitorProcessGroup
   
   User can select modules to monitor. It comunicates using rest api with Apache Nifi to pull bulletins and drop events on monitored modules.
   Monitor Bulletins part has been developed using JSON Processors. JSON is transformed to smaller object using JOLT, filtered and splitted from an array to multiple flow files.
   
   There are possible processors where DROP is allowed:
   - Processor without outgoing connection.
   - Processor with terminated success status.
   - Processor types like "SplitJson".
   These processors will be monitored just for bulletins.
