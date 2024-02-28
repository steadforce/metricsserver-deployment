# Metrics Server

Repository containing manifests for [Metrics Server](https://github.com/kubernetes-sigs/metrics-server).
Never install the content of this repo on our clusters manually. This is all done by argocd.

Note: metrics-server is currently only used in the local (KinD) cluster.

## Dependencies

This chart pulls in `metrics-server` as a dependency. The version
used is specified in `Chart.yaml` in the `dependencies` section.
If you change the version in there, you need to then run

    $ helm dependency update

in order to have the chart downloaded to the `charts` directory
and then also commit that new version alongside with the altered
`Chart.yaml` file.

See the [Helm docs](https://helm.sh/docs/topics/charts/#chart-dependencies)
for details.

## Render resources like argo-cd locally

```
 helm template \
      --release-name metrics-server \
      -n metrics-server \
      --include-crds \
      --skip-tests \
      -f values-kind.yaml \
      --output-dir _local .
```