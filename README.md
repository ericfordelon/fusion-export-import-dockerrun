
Copy the sample application properties into application.properties
```
cp config/sample.application.properties config/application.properties
```

Perform a docker pull to get the latest version of the repository
```
docker pull ericfordelon/fusion-export-import
```
# Example Commands
Export an app named test from Dev Server to Local directory
```
docker run \
-v $(pwd)/config:/config \
-v $(pwd)/exports:/exports \
ericfordelon/fusion-export-import \
--appName=test \
--sourceType=server --sourceEnvironment=dev \
--destinationType=file --destinationEnvironment=dev \
ExportImport
```

Clones an app named test from Dev Server to Local directory where the new cloned App should be named test_$(SOME_RANDOM_NUMBER)
```
docker run \
-v $(pwd)/config:/config \
-v $(pwd)/exports:/exports \
ericfordelon/fusion-export-import \
--appName=test \
--sourceType=server --sourceEnvironment=dev \
--destinationType=file --destinationEnvironment=dev \
--cloneAppName=test_$(date '+%s') \
Clone
```

Clones an app named test from Dev Server to Dev Server where the new cloned App should be named test_$(SOME_RANDOM_NUMBER)
```
docker run \
-v $(pwd)/config:/config \
-v $(pwd)/exports:/exports \
ericfordelon/fusion-export-import \
--appName=test \
--sourceType=server --sourceEnvironment=dev \
--destinationType=server --destinationEnvironment=dev \
--cloneAppName=test_$(date '+%s') \
Clone
```
