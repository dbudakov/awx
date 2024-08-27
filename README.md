
ansible-galaxy collection install -r requirements.yml
ansible-galaxy install -r requirements.yml

```txt
~/.kube/config
* unable to read client-cert /home/vagrant/.minikube/profiles/minikube/client.crt for minikube due to open /home/vagrant/.minikube/profiles/minikube/client.crt: no such file or directory
* unable to read client-key /home/vagrant/.minikube/profiles/minikube/client.key for minikube due to open /home/vagrant/.minikube/profiles/minikube/client.key: no such file or directory
* unable to read certificate-authority /home/vagrant/.minikube/ca.crt for minikube due to open /home/vagrant/.minikube/ca.crt: no such file or directory
```


https://ansible.readthedocs.io/projects/awx-operator/en/latest/#get-involved
https://github.com/ansible/awx-operator/tree/devel
https://www.jeffgeerling.com

https://ansible.readthedocs.io/projects/awx-operator/en/latest/installation/creating-a-minikube-cluster-for-testing.html

## helm chart
https://ansible-community.github.io/awx-operator-helm/

```bash
helm repo add awx-operator https://ansible-community.github.io/awx-operator-helm/
helm install my-awx-operator awx-operator/awx-operator
# my-values.yml: https://raw.githubusercontent.com/ansible/awx-operator/2.19.1/awx-demo.yml
# helm install my-awx-operator awx-operator/awx-operator -n awx --create-namespace -f my-values.yml --version 1.3.0
# helm delete my-awx-operator
```

```bash
vagrant up && vagrant halt && vagrant up --provision
```


```bash
# minikube start --cpus=4 --memory=6g --addons=ingress
```

```bash
vagrant ssh
minikube service awx-service
"http://192.168.49.2:32246" >> ./roles/nginx/conf/awx.conf
```

### vault
```bash
export VAULT_ADDR='http://127.0.0.1:8200'
export VAULT_TOKEN=$(docker exec vault sh -c "cat /home/vault/.vault-token")
vault token lookup 

# for awx.lab
# Type Details -> Server URL * 
http://192.168.49.5:8200

# Token 
VAULT_TOKEN

# добавить путь к секрету в credentials
# добавить секрет к job_template

# vault add secret
vault token lookup # vault token lookup -format json  | jq -r .data.id
vault secrets enable -path=secret/ kv
vault kv put -mount=secret hello foo=world excited=yes


```

### vector


### metrics


### other
vagratn 2.4.1 -> http://vagrant.krsnv.ru/2.4.1/
https://vagrant.elab.pro/downloads/


logger_name: awx.analytics.job_events
job: 8

### minikube dashboard
```bash
# https://thenewstack.io/how-to-enable-and-use-the-minikube-dashboard/
minikube dashboard --url --port=8081
kubectl proxy --address='0.0.0.0' --accept-hosts='^*$' --port=8080
192.168.0.111:8080/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
```

### color AWX (false)

<!-- https://docs.ansible.com/ansible-tower/latest/html/towercli/output.html -->
helm pull awx-operator/awx-operator



vault create secrets
keycloak
exception 500 awx

apply keycloak and awx auth
apply dashboard 
apply discover elastic

helm chart download


/opt/keycloak/bin/kc.sh export --realm lab --file /tmp/export
 /opt/keycloak/bin/kc.sh import --file /tmp/export 




 secret vault
 определить cred
 привязать кред в template

### metrics
```bash
# perfomance: time for commit to DB
# HELP task_manager_commit_seconds Time spent in db transaction, including on_commit calls
# TYPE task_manager_commit_seconds gauge
task_manager_commit_seconds{node="awx-task-786c84cf49-c2l6n"} 0.0003204345703125

# perfomance: time for pending
# HELP dependency_manager_get_tasks_seconds Time spent loading pending tasks from db
# TYPE dependency_manager_get_tasks_seconds gauge
dependency_manager_get_tasks_seconds{node="awx-task-786c84cf49-c2l6n"} 0.0031810149998818815
```