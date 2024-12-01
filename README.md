# first-kubernetes-operator

K8s Operators practice with Kubebuilder

## Prerequisites

- [Go](https://go.dev/)
- [Orbstack](https://orbstack.dev/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [Openlens](https://formulae.brew.sh/cask/openlens)
- [Openlens Node Pod Menu Extension](https://medium.com/geekculture/fix-essential-functionality-missing-in-the-new-openlens-version-f9ac862e9e27)

## Resources

- [Kubebuilder Book](https://book.kubebuilder.io/quick-start.html)
- [Kubebuilder API design](https://book.kubebuilder.io/cronjob-tutorial/api-design)
- [Kubebuilder What's in a controller](https://book.kubebuilder.io/cronjob-tutorial/controller-overview)

## Install kubebuilder

```bash
curl -L -o kubebuilder "https://go.kubebuilder.io/dl/latest/$(go env GOOS)/$(go env GOARCH)"
chmod +x kubebuilder && sudo mv kubebuilder /usr/local/bin/
```

## Create a new operator

```bash
mkdir first-kubernetes-operator
cd first-kubernetes-operator
kubebuilder init --domain mydomain.com --repo mydomain.com/first-kubernetes-operator
```

```bash
# Create an API
kubebuilder create api --group mydomain --version v1 --kind MyKind
```

- Add logic to the `Reconcile` function in the `internal/controller/{kind-name}_controller.go´` file
- Add fields to the Spec struct in the `api/v1/{kind-name}_types.go` file
- Add fields to the `config/samples/{...kind-name}.yaml` file

```bash
# Generate the manifests
make manifests

# Get kubernetes cluster info
kubectl cluster-info

# Install the CRDs into the cluster
make install

# Run the operator for development
make run

# Install instances of CRs
kubectl apply -k config/samples/

# Uninstall instances of CRs
kubectl delete -k config/samples/

# Build controller and push to image registry (IMG)
make docker-build docker-push IMG=<some-registry>/<project-name>:tag

# Deploy controller to the cluster with image
make deploy IMG=<some-registry>/<project-name>:tag
```
