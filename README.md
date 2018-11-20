# Exercise 6 - Kubernetes & Helm

## 1. Prepare the basic deployment of the ICNDB application

To be able to run the ICNDB application a `Deployment` is required running the pre-built container image [baez90/jericho-victim](https://hub.docker.com/r/baez90/jericho-victim) based on the source code on [GitHub](https://github.com/baez90/SA-Jericho).
The application needs a PostgreSQL database as you can see in the shipped Docker-Compose files.

1. Prepare the `deployment.yaml` for the application
    1. ICNDB container
    2. PostgreSQL container
    3. Environment variables corresonding to the Docker-Compose files
2. Prepare the `service.yaml` adapting the container port from your deployment
3. Prepare the `ingress.yaml`
4. Validate your templates by calling `helm lint`
5. Check the generated YAML files by calling `helm template`
6. Deploy your chart to a Kubernetes

## 2. Declare a dependency

In the first part every instance (pod) of the ICNDB ships with it's own PostgreSQL.
That's kinda overhead so it seems to be a good idea to reduce the overhead by declaring a dependency to the public PosgreSQL chart.

1. Create a `requirements.yaml`
2. Delcare a dependency to the official PostgreSQL chart
3. Use `helm dependency` to manage the dependencies
4. Check how to delegate values from the parent to the child chart
5. Upgrade your deployment to the new version based on a dependendant chart