Frack Submitter
===============

What is it?
-----------

The submitter is used to submit Pipelines to the Frack ingest system. It can be run both as a local executable and
a Thrift service.

Running in Local Mode
---------------------

When running in local mode, the Submitter executable expects the following:

* a jar with dependencies containing the pipeline code
* a folder in the current directory called 'conf' containing all site properties files
* a folder in the current directory called 'user-conf' with subdirectories for each pipeline containing user configuration files
* the frack-submitter.json file in the current directory
* the ezbroadcast-redis jar with dependencies in the current directory
* a redis instance up and running, with connection information in the configuration files in the conf directory
* a zookeeper instance up and running, with connection information in the configuration files in the conf directory

In order to submit a jar to the submitter in local mode, run the submitter with the following command:

`java -jar frack-submitter.jar -p <pipeline jar> -n`

The -n command line argument signifies that the messages broadcast with the pipeline will not be secured. If you wish
to have message secured locally and have authorization checking, then the security service must also be running.

Running the Thrift Service
--------------------------

The submitter should not be run as a service locally. It is intended only for use on a cloud infrastructure. When submitting
pipelines in the cloud, the ezDeploy service should be leveraged along with OpenShift.
