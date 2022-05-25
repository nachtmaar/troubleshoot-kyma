# trouble-shoot kyma

This repository is a playground for playing with `troubleshoot` and `sbctl`.
I compiled a preflight check and a simple troubleshoot definition for Kyma eventing.

## How to use it

Install it:
```shell
# install via krew
# source: https://troubleshoot.sh/docs/
kubectl krew install preflight
kubectl krew install support-bundle
```

Run it:
```
# run it
kubectl preflight ./preflight.yaml
kubectl support-bundle ./support-bundle.yaml
```

Check also the support-bundle which was generated:
```shell
$ mkdir support-bundle
$ tar xf support-bundle-2022-05-25T10_43_50.tar.gz -C support-bundle
$ tree -L 1 .
.
├── analysis.json
├── cluster-info
├── cluster-resources
├── configmaps
├── eventing-controller-f89859b5b-r4zvc
├── eventing-publisher-proxy-5d94c6f5c9-xk55j
├── secrets
└── version.yaml

6 directories, 2 files
```

View the support-bundle using kubectl:
```
# source: https://github.com/replicatedhq/sbctl
sbctl serve --support-bundle-location support-bundle-2022-05-25T10_43_50.tar.gz &
export KUBECONFIG=/var/folders/g2/XXXXXXXXXXX/T/local-kubeconfig-XXXXX
```


## Links

<https://github.com/replicatedhq/troubleshoot>
<https://troubleshoot.sh/docs/>
