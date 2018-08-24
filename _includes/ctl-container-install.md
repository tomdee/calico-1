## Installing calicoctl as a container on a single host

To install `calicoctl` as a container on a single host, log into the
target host and issue the following command.

```
docker pull {{site.imageNames["calicoctl"]}}:{{site.data.versions.first.title}}
```

**Next step**:

[Configure `calicoctl` to connect to your datastore](/usage/calicoctl/configure/).


## Installing calicoctl as a Kubernetes pod


Use the YAML that matches your datastore type to deploy the `calicoctl` container to your nodes.

- **etcd**

   ```
   kubectl apply -f \
   {{site.url}}/getting-started/kubernetes/installation/hosted/calicoctl.yaml
   ```

   > **Note**: You can also
   > [view the YAML in a new tab]({{site.url}}/getting-started/kubernetes/installation/hosted/calicoctl.yaml){:target="_blank"}.
   {: .alert .alert-info}

- **Kubernetes API datastore**

   ```
   kubectl apply -f \
   {{site.url}}/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calicoctl.yaml
   ```

   > **Note**: You can also
   > [view the YAML in a new tab]({{site.url}}/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calicoctl.yaml){:target="_blank"}.
   {: .alert .alert-info}

You can then run commands using kubectl as shown below.

```
kubectl exec -ti -n kube-system calicoctl -- /calicoctl get profiles -o wide

NAME                 TAGS
kns.default          kns.default
kns.kube-system      kns.kube-system
```