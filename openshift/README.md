Creating resources
```bash
oc run newpod --image=registry.redhat.io/rhel8/httpd-24
oc apply -f filename.yaml
oc create -f filename.yaml
cat filename.yaml | oc create -f -
```
```bash
oc run newpod --image=registry.redhat.io/rhel8/httpd-24
oc run newpod --image=registry.redhat.io/rhel8/httpd-24 --dry-run=client -o yaml
oc run newpod1 --image=registry.redhat.io/rhel8/httpd-24 --restart=Never
oc run newpod2 --image=registry.access.redhat.com/ubi9/ubi --restart=Never --command -- sleep 3600
oc run newpod2 --image=registry.access.redhat.com/ubi9/ubi --restart=Never --command -- sleep 3600
oc run newpod2 --image=registry.access.redhat.com/ubi9/ubi --restart=Never --command -- sleep 3600 --env MYSQL_ROOT_PASSWORD=myP@$$123
oc rsh newpod2
oc cp /tmp/index.html pod-name:/var/www/html/
oc rsync pod-name:/var/www/ /tmp/web_files
oc exec -it newpod2 -- /bin/bash
oc logs podname
oc logs podname --tail=10
oc delete pod podname
oc delete pod podname --grace-period=10
oc delete pod podname --now
oc delete pod podname --force
oc delete pod --all -n namespacename
oc delete pod -l app=appname
oc delete pod -f file.yaml
cat file.yaml | oc delete -f -
cat file.yaml | oc create -f -
oc get events
oc get ev -A --sort-by='.lastTimestamp'
```
Deployment commands
```bash
oc create deployment myapp --image=registry.redhat.io/rhel8/httpd-24
oc get deploy
oc scale deploy myapp --replicas=3
oc rollout status deploy/myapp
oc rollout history deploy/myapp
oc set image deploy/myapp  httpd-24=registry.redhat.io/rhel9/httpd-24
oc rollout undo deploy/myapp --to-revision=2
oc rollout status deploy/myapp
oc rollout history deploy/myapp
oc describe deployment myapp|grep -i revision
```
Service commands

oc create service nodeport demo-nodeport --tcp=9999:8080
oc edit service nodeport
oc get endpoints demo-nodeport
