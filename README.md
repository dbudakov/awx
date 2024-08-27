# AWX BOX

### accounts

- _https://awx.lab_: awx:awx
- _https://keycloak.lab_: admin:admin
- _https://vault.lab_: token -> my_token
- _https://grafana.lab_: admin:admin
- _https://prometheus.lab_: free

### vault

```bash
export VAULT_ADDR='http://127.0.0.1:8200'
export VAULT_TOKEN=$(docker exec vault sh -c "cat /home/vault/.vault-token") # VAULT_TOKEN=my_token
vault token lookup 

# Type Details -> Server URL * 
http://192.168.49.5:8200

# vault add secret
vault token lookup # vault token lookup -format json  | jq -r .data.id
vault secrets enable -path=secret/ kv
vault kv put -mount=secret custom example=hello_world!
```

### minikube dashboard

```bash
# https://thenewstack.io/how-to-enable-and-use-the-minikube-dashboard/
minikube dashboard --url --port=8081
kubectl proxy --address='0.0.0.0' --accept-hosts='^*$' --port=8080
192.168.0.111:8080/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
```

### DEMO
```
# добавить путь к секрету в credentials
# добавить секрет к job_template
```

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

### kibana: visual
- logger_name: awx.analytics.job_events, job: 8
