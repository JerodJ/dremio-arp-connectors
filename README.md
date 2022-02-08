# CData Dremio Connector Template

This template allows you to create an ARP Connector for any CData JDBC Driver. To modify the files and contents, you will need to know the class name for the JDBC Driver (referred to as *ClassName* going forward). For example: the CData JDBC Driver for Amazon DynamoDB has the class name *AmazonDynamoDB*. Use *ClassName* for any mixed cases instances and *classname* for any lowercase instances.

## Edit Filenames

Rename the following files:

* DatasourceConf.java becomes ClassNameConf.java (example: *AmazonDynamoDBConf.java*)
* datasource-layout.json becomes classname-layout.json (example: *amazondynamodb-layout.json*)
* datasource-arp.yaml becomes classname-arp.yaml (example: *amazondynamodb-arp.yaml*)

## Edit File Contents

Edit the contents of the files (*pom.xml*, *ClassNameConf.java*, *classname-arp.yaml*, and *classname-layout.json*):

* Find {Datasource} and replace it with ClassName (example: *AmazonDynamoDB*)
* Find {DatasourceLower} and replace it with classname (example: *amazondynamodb*)

## Build the ARP Connector

Run the following command in the root directory for the Connector (the connector that contains the *pom.xml* file):

    mvn clean install
    
## Copy the ARP Connector & JDBC Driver JAR Files

Copy the ARP Connector JAR file the /jars/ directory of your Dremio installation:

    docker cp PATH\TO\dremio-classname-plugin-20.0.0.jar dremio_image_name:/opt/dremio/jars/

Copy the JDBC Driver to the /jars/3rdparty/ directory of your Dremio installation:

    docker cp PATH\TO\cdata.jdbc.classname.jar dremio_image_name:/opt/dremio/jars/3rdparty/
