### Maven/Docker/OpenShift

Run the "Hello World!" app:

```
mvn clean install
pushd hello-api/; mvn spring-boot:run; popd
```

Build the `jar`:

```
mvn package
```

Build locally with Docker:

```
docker build hello-api/ -t hello-api:latest
```

Build on OpenShift (maybe via a Jenkins slave pod):

```

# assume your in project `hello-test`
# create the build config

oc process -f templates/build.yml \
   -p ENVIRONMENT=test \
   -p APPLICATION=hello \
   -p COMPONENT=api \
   -p TAG_VERSION=latest | oc apply -f -
   
   
# upload archive of module with Dockerfile and jar,
# build and push image to openshift registry

oc start-build hello-api-latest \
   --from-dir hello-api/ \
   --follow
```