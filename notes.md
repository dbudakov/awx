
### task list

- vault create secrets
- apply dashboard 
- apply discover elastic
- helm chart download


secret vault
определить cred
привязать кред в template


### color AWX (false)

<!-- https://docs.ansible.com/ansible-tower/latest/html/towercli/output.html -->
helm pull awx-operator/awx-operator

### vagrant update version
vagratn 2.4.1 -> http://vagrant.krsnv.ru/2.4.1/
https://vagrant.elab.pro/downloads/

### keycloak

```bash
# export import realm
/opt/keycloak/bin/kc.sh export --realm lab --file /tmp/export
/opt/keycloak/bin/kc.sh import --file /tmp/export 
```

### links

- [](https://ansible.readthedocs.io/projects/awx-operator/en/latest/#get-involved)
- [](https://github.com/ansible/awx-operator/tree/devel)
- [](https://www.jeffgeerling.com)
- [ansible_minkube](https://ansible.readthedocs.io/projects/awx-operator/en/latest/installation/creating-a-minikube-cluster-for-testing.html)
- [helm_chart](https://ansible-community.github.io/awx-operator-helm/)