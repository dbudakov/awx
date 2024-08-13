
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