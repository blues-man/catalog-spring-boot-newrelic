# New Relic agent integration on OpenShift

Example on how to integrate New Relic into a Springboot application on OpenShift, using [Red Hat Coolstore app](https://github.com/jbossdemocentral/coolstore-microservice):



## Create s2i structure

Create a dir in the root of your Springboot application `.s2i/bin`

```shell
$ mkdir -p .s2i/bin
```

Copy [assemble](https://github.com/blues-man/catalog-spring-boot-newrelic/blob/master/.s2i/bin/assemble) and [run](https://github.com/blues-man/catalog-spring-boot-newrelic/blob/master/.s2i/bin/run) script there


```shell
$ curl -o .s2i/bin/assemble https://raw.githubusercontent.com/blues-man/catalog-spring-boot-newrelic/master/.s2i/bin/assemble
```

```shell
$ curl -o .s2i/bin/run https://raw.githubusercontent.com/blues-man/catalog-spring-boot-newrelic/master/.s2i/bin/run
```

## Create s2i app

```shell
oc new-app --build-env NEWRELIC_APPNAME=<YOUR_APP_NAME> --build-env NEWRELIC_LICENSE=<YOUR_LICENSE_KEY> openshift/redhat-openjdk18-openshift:1.4~<YOUR_GIT_URL>
```

Example with Catalog app from Red Hat Coolstore:
```shell
oc new-app --build-env NEWRELIC_APPNAME=catalog-springboot-openshift --build-env NEWRELIC_LICENSE=<YOUR_LICENSE_KEY> openshift/redhat-openjdk18-openshift:1.4~https://github.com/blues-man/catalog-spring-boot-newrelic
```


