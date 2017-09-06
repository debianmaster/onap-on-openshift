# ONAP on openshift

```console
setenforce 0   #hate to do this but....
#login as cluster-admin

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

