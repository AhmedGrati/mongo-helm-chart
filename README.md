# mongo-helm-chart
This is a MongoDB chart that will be used to store Graylog configurations
# Getting Started
To install this chart, run the following commands:
1. Create a database namespace, by running this command:
```shell
kubectl create ns database
```
2. Pull the dependencies of this chart, by running this command:
```shell
kubectl dependency update ./mongo-helm-chart
```
3. Create a secret that will hold the password of the mongodb database. It should look like this:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: mongodb-secret
data:
  mongodb-passwords: ZHVtbXk=
  mongodb-root-password: ZHVtbXk=
```
4. Create a folder in your node that will hold data of mongodb.
```shell
mkdir -p /kubernetes-persistent-volume/mongodb/
```
5. Install the chart:
`helm install mongodb mongo-helm-chart -f mongo-helm-chart/values.yaml -n database`
