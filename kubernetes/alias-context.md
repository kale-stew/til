# Aliasing Contexts in Kubectl

I was navigating a variety of environments, each requiring numerous config steps prior to a successful deployment. Scripting this was made way easier when I began to alias the environments into their own `context` within `kubectl`.

If you are unfamiliar, [here](https://kubernetes.io/docs/reference/kubectl/overview/) is some background on the Kubernetes CLI `kubectl`.

To create a `prod` config context for the project `quoteboard` in cluster `my-cluster`

```sh
gcloud config set project quoteboard-prod
gcloud container clusters get-credentials my-cluster
kubectl config set-context prod --user=cluster-admin --namespace=production
```

To confirm your context was created with the correct credentials

```sh
# list the current context
kubectl config current-context

# check out pods running in a specific context
kubectl get pods --context=prod
```

To use your context, throw the flag into any standard `kubectl` command

```sh
# like a deployment
kubectl apply -f deploy.yaml --context=prod

# or describing secrets
kubectl --context=prod config view -o=yaml
```
