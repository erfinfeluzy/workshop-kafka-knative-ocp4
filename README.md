# Workshop Kafka Knative on OCP 4
This tutorial will show step by step Kafka & Knative demo using RH Integration stack

## Prerequisite
1. preinstalled ocp 4. can use RH CodeReady Containers (CRC)
2. preinstalled RH Openshift Serverless
3. Optional. preinstalled oc client on student's workstation

## Step 0: Create new Project
1. on top bar. Project > Create Project > project name = student-XX-demo
> change XX to your user number

## Step 1: Install Red Hat AMQ Stream (Kafka) using Operator
This steps need cluster admin level role
1. Login ocp web console 
2. open Administrator Dashboard > Operators > Operator Hub. search "AMQ Streams" > Install
3. open Administrator Dashboard > Operators > Installed Operator > AMQ Streams > Kafka > Create Instance
4. AMQ Stream will be installed on project : **student-XX-demo** 

## Step 2: Install Kafka producer sample apps as normal deployment
Sample apps using Quarkus. source code [here](https://github.com/erfinfeluzy/quarkus-kafka-producer)
1. Open Developer Dashboard > Topology > right click > Add to Project > Container Image
2. choose radio button : **Image name from external registry**
3. input: **quay.io/efeluzy/quarkus-kafka-producer:v3**
4. resource (combobox): Deployment
5. uncheck **Create a route to the application**

## Step 3: Install Kafka consumer sample apps as knative deployment
Sample apps using Quarkus. source code [here](https://github.com/erfinfeluzy/quarkus-kafka-consumer)
1. Open Developer Dashboard > Topology > right click > Add to Project > Container Image
2. choose radio button : **Image name from external registry**
3. input: **quay.io/efeluzy/quarkus-kafka-consumer:v3**
4. resource (combobox): Knative Service
5. Check **Create a route to the application**

## Step 4: Open Kafka consumer sample apps Route
1. Open Developer Dashboard > Topology > on ksvc service **quarkus-kafka-consumer** > open URL
2. on browser open $URL/stream

## Result on OCP
Deployment will be like this on Openshift web console. Developer dahsboard > topology.
