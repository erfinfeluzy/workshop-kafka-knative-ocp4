# Workshop Deploy Serverless Apps on OpenShift 4
This tutorial will show how to deploy serverless apps demo using Red Hat OpenShift 4

## Prerequisite
1. Preinstalled OpenShift Container Platform 4. we can use RH CodeReady Containers (CRC) for local purpose.
2. Preinstalled RH Openshift Serverless.
3. Optional: preinstalled oc client on student's workstation

## Step 1: Create new Project
1. on top bar. Project > Create Project > project name = student-XX-demo
> change XX to your user number
![result](https://github.com/erfinfeluzy/ocp4-notes/blob/master/screenshot/deploy-knative-apps-create-ns.png)

## Step 2: Install sample apps from container registry as serverless application

Note: Sample apps is using Java application Quarkus. source code [here](https://github.com/erfinfeluzy/quarkus-kafka-consumer)
1. Open Developer Dashboard > Topology > right click > Add to Project > Container Image
![result](https://github.com/erfinfeluzy/ocp4-notes/blob/master/screenshot/deploy-knative-apps-0.png)
2. choose radio button : **Image name from external registry**
3. input: **quay.io/efeluzy/quarkus-rest-health:v1**
![result](https://github.com/erfinfeluzy/ocp4-notes/blob/master/screenshot/deploy-knative-apps-1.png)
4. resource (combobox): Knative Service
5. Check **Create a route to the application**
![result](https://github.com/erfinfeluzy/ocp4-notes/blob/master/screenshot/deploy-knative-apps-2.png)

## Step 4: Open sample apps Route
1. Open: Developer Dashboard > Topology > on ksvc service **quarkus-rest-health** > open URL
2. on browser open $URL/health
3. Close browser. idle untill the pods size scaled to Zero (0)
![result](https://github.com/erfinfeluzy/ocp4-notes/blob/master/screenshot/deploy-knative-apps-4.png)
4. Reopen the browser: Developer Dashboard > Topology > on ksvc service **quarkus-rest-health** > open URL
5. Pod will scale from 0 to 1 when request received.

## Result on OCP
Deployment will be like this on Openshift web console. Developer dahsboard > topology.
![result](https://github.com/erfinfeluzy/ocp4-notes/blob/master/screenshot/deploy-knative-apps-3.png)
