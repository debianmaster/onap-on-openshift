# ONAP on openshift
> ONAP installation scripts require a shared volume (PV) for reading all the configuration files  and the install scripts are reading it from a hostPath volume. Due to this reason we require hostPath volumes to be enabled on the openshift namespace/cluster.   This required all the components of the application needed to be running on single machine and also selinux disabaled.    In future we can refactor scripts to utilize a PV that may be part of gluster volume but for now disable selinux and make the service account privileged.

## Login and Pre-req
```console
setenforce 0    #Had do this for enabling hostPath volumes
# Login as cluster-admin     
# You need a machine with atleast 32+ GB of memory
```
## Make default service account privileged in all namespaces
> For hostPath mounts service account needs to have privileged scc. 
> ONAP instal scripts create a bunch of namespaces for components. The docker images involved in these deployments seem to use uid 0 which is by default blocked by openshift so as to avoid any container security issues. until we refactory these images to use non 0 uid users we need to bypass this feature.
> Also some components are in need of cluster wide privileges so cluster-admin privileged is added.

```console
for ns in onap-aai onap-appc onap-message-router onap-mso onap-policy onap-vid onap-portal onap-robot onap-sdc onap-sdnc onap-sdnconap-vid 
do
  oc adm policy add-scc-to-user privileged -z default -n $ns
  oc adm policy add-scc-to-user hostmount-anyuid -z default -n $ns
  oc adm policy add-scc-to-user anyuid -z default -n $ns
  oc adm policy add-cluster-role-to-user cluster-admin -z default -n  $ns
done
```


### Deploying ONAP
> script are available at this location  
`git clone -b release-1.0.0 http://gerrit.onap.org/r/oom `
> k8s specific scripts are located in this folder   
```
cd oom/kubernetes/config/    
chmod +x ./createConfig.sh
```

> This step is going to generate all the required configuration files and shared via hostPath volume 
`./createConfig.sh -n onap`

> This script will create all the required components like deployments,services etc   
cd ../oneclick/
`./createAll.bash -n onap`

### Wait for ~ 15-30 mins
> ONAP has failry large number of components, each of these components are using init containers to see if the required dependent components are available. so this deployment is taking good amount of time for completion based on speed of internet. So give it some time and watch for failures.  if something is failed too many times, take a look at log. either at docker daemon level or k8s events
