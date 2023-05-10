# FileNet Salesforce Integration in ROKS environment
To integrate FileNet and Salesforce we use a tool called IBM FileNet Content Manager Connector for Salesforce. It is available in the Salesforce Marketplace. In Order for your configuration to be successful you need to make a few modifications in the Nginx pod, GraphQL pod.

* Go to workloads --> pods --> Search for ibm-nginx(click the one that does not contain tester)
NB: make sure CP4BA is the selected project
* Go to terminal tab
* modify the cp4ba-graphql-zen-extension.conf
`vi /user-home/_global_/nginx-conf.d/cp4ba-graphql-zen-extension.conf`
* Download cp4ba-graphql-zen-extension.conf file and copy the content to your ibm-nginx cp4ba-graphql-zen-extension.conf
* Delete both ibm-nginx pods(not ibm-nginx test pod)

**CORS**
* Search for cp4ba-graphql pod
* Create a cors.xml in the following directory configDropins/overrides
`vi configDropins/overrides/cors.xml`
* Download and copy the cors.xml
* Add your Salesforce URL in allowedOrigins e.g. allowedOrigins=example.sandbox.lightning.force.com
* Add your self-signed certificate (IBMFileNetCertificate.crt) downloaded from Salesforce to this path: `cd configDropins/overrides/`

For the rest of the configuration follow the provided documentation.








