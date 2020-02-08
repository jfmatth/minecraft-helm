# Minecraft for Kubernetes - HELM

Using the HELM chart for Minecraft, this is a values file that I use for flexibity.  Some changes:

- Extend the start up time for the healthcheck
- Change the memory
- Add my son as the operator (Admin) of the server
- Set the version using this site https://minecraft.gamepedia.com/Java_Edition_version_history


## Using this repo

Using this repo / chart https://github.com/helm/charts/tree/master/stable/minecraft

```
helm install --name minecraft stable/minecraft -f values.yaml
```

Depending on the environment, the world might take 3 - 4 min to generate.  Find the pod that is the world and watch the logs.