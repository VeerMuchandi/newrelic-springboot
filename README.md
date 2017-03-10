## Template to use NewRelic with SpringBoot

This example shows how to create a SpringBoot application that can be monitored using New Relic.

We will use a CentOS Java container image with New Relic java agent baked in. Here is one that I created docker.io/veermuchandi/springboot-newrelic-centos based on the spring boot example from [https://github.com/codecentric/springboot-maven3-centos.git](https://github.com/codecentric/springboot-maven3-centos). I edited this code to include the java agent and the the code is here [https://github.com/VeerMuchandi/springboot-newrelic-centos](https://github.com/VeerMuchandi/springboot-newrelic-centos)

####Usage

**Step 1** Create a new project

```
oc new-project myproject
```
**Step 2** Add this New Relic + Java image-stream to your project.

```
oc create -f 
```
Alternately, you can add this to the openshift namespace, if you want this accessible across all the projects.

**Step 3** Add the template to your project. This allows you create your Spring Boot application easily.

```
oc create -f 
```

**Step 4** Deploy your application	

Go to OpenShift Web Console, find the template with name `springboot-newrelic` and use it.

You will have to fill the following parameters to create your application.		
1. `APPLICATION_NAME` - Name of your application on OpenShift		
2. `NEWRELIC_APPNAME` - Name of your application on New Relic		
3. `NEWRELIC_ENCODED_LICENSE` - Base64 encoded value of your license key. You can encode it here [https://www.base64decode.org/](https://www.base64decode.org/). The template will create a secret using this license key and mount it during the build process.		 	
4. `GIT_URI` - The git URI for your Spring Boot source code			

There are a few other optional parameters that you can change as per your needs.

OpenShift will build and deploy this application.



