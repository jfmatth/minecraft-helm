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

## Keeping your world and updating the values.yaml

Assuming you want to add say your son to the values list as an operator, and you want to save the running world.  
- update the values.yaml file 
- scale down the existing running deployment to 0 (I find this to be best so you don't have two pods running)
```
kubectl scale --replicas=0 deploy/minecraft-minecraft
```
- update the helm chart
```
helm upgrade minecraft stable/minecraft -f values.yaml
```
- Scale back up to redeploy a new updated pod with the same world
```
kubectl scale --replicas=1 deploy/minecraft-minecraft
```
