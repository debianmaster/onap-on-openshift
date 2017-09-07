# ONAP on openshift

```console
setenforce 0   #hate to do this but....
# Login as cluster-admin
# You need a machine with atleast 32+ GB of memory

oc adm policy add-scc-to-user privileged -z default -n onap
oc adm policy add-scc-to-user anyuid -z default -n onap
oc adm policy add-scc-to-user privileged -z default -n onap-aai
oc adm policy add-scc-to-user privileged -z default -n onap-appc
oc adm policy add-scc-to-user privileged -z default -n onap-message-router
oc adm policy add-scc-to-user privileged -z default -n onap-mso
oc adm policy add-scc-to-user privileged -z default -n onap-policy
oc adm policy add-scc-to-user privileged -z default -n onap-portal
oc adm policy add-scc-to-user privileged -z default -n onap-robot
oc adm policy add-scc-to-user privileged -z default -n onap-sdc
oc adm policy add-scc-to-user privileged -z default -n onap-sdnc
oc adm policy add-scc-to-user privileged -z default -n onap-vid
oc adm policy add-scc-to-user anyuid -z default -n onap-vid
oc adm policy add-scc-to-user anyuid -z default -n onap-sdnc
oc adm policy add-scc-to-user anyuid -z default -n onap-robot
oc adm policy add-scc-to-user anyuid -z default -n onap-portal
oc adm policy add-scc-to-user anyuid -z default -n onap-policy
oc adm policy add-scc-to-user anyuid -z default -n onap-mso
oc adm policy add-scc-to-user anyuid -z default -n onap-message-router
oc adm policy add-scc-to-user anyuid -z default -n onap-appc
oc adm policy add-scc-to-user anyuid -z default -n onap-aai


oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-vid
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-sdnc
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-robot
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-portal
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-policy
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-mso
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-message-router
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-appc
oc adm policy add-scc-to-user hostmount-anyuid -z default -n onap-aai


oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-vid
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-sdnc
onap-sdc
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-robot
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-portal
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-policy
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-mso
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-message-router
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-appc
oc adm policy add-cluster-role-to-user cluster-admin -z default -n onap-aai



git clone -b release-1.0.0 http://gerrit.onap.org/r/oom
cd oom/kubernetes/config/
chmod +x ./createConfig.sh
./createConfig.sh -n onap
cd ../oneclick/
./createAll.bash -n onap

# Wait for 30 min .... yes !
```




#### Work-in-progress for k8s
```

    kubectl create clusterrolebinding rule1 --clusterrole=cluster-admin --serviceaccount=onap:default
    kubectl create clusterrolebinding rule1 --clusterrole=cluster-admin --serviceaccount=onap-vid:default
    kubectl create clusterrolebinding rule2 --clusterrole=cluster-admin --serviceaccount=onap-sdnc:default
    kubectl create clusterrolebinding rule3 --clusterrole=cluster-admin --serviceaccount=onap-robot:default
    kubectl create clusterrolebinding rule4 --clusterrole=cluster-admin --serviceaccount=onap-portal:default
    kubectl create clusterrolebinding rule5 --clusterrole=cluster-admin --serviceaccount=onap-policy:default
    kubectl create clusterrolebinding rule6 --clusterrole=cluster-admin --serviceaccount=onap-mso:default
    kubectl create clusterrolebinding rule7 --clusterrole=cluster-admin --serviceaccount=onap-message-router:default
    kubectl create clusterrolebinding rule8 --clusterrole=cluster-admin --serviceaccount=onap-appc:default
    kubectl create clusterrolebinding rule9 --clusterrole=cluster-admin --serviceaccount=onap-aai:default
 ```
