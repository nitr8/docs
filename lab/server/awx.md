# Ansible AWX

AWX provides a web-based user interface, REST API, and task engine built on top of Ansible. It is one of the upstream projects for Red Hat Ansible Automation ...

## Installing AWX on K3S

```bash

sudo systemctl disable firewalld --now
sudo dnf -y install git curl

2.) Disable the fw: sudo systemctl disable firewalld --now
3.) Install git & curl: sudo yum -y install git curl
4.) Install k3s: curl -sfL https://get.k3s.io | INSTALL_K35_VERSION=v1.28.6+k352 sh-s - --write-kubeconfig-mode 644
sudo k3s kubectl get node # Check for Ready node, takes ~30 seconds 

5.) Install AWX Operator:
cd ~
git clone https://github.com/kurokobo/awx-on-k3s.git
cd awx-on-k3s
git checkout 2.12.2
6.) deploy awx operator: kubectl apply -k operator
7. Check on AWX operator deployment: kubectl -n awx get all
8. ) set hostname and create ssl keys:
AWX_HOST="temp-awx.maddog. local"
openssl req -×509 -nodes -days 3650 -newkey rsa:2048 -out ./base/tls.crt -keyout ./base/tls.key -subj "/CN=
${AWX_HOST}/0=${AWX_HOST}" -addext "subjectAltName = DNS:${AWX.
_HOST}"
9.) Edit hostname in base/awx.yaml
10. ) Edit base/kustomization.yaml
11.) Create directories and set permisions:
sudo mkdir -p /data/postgres-13 sudo mkdir -p /data/projects sudo chmod 755 /data/postgres-13 sudo chown 1000:0 /data/projects
12.) deploy AWX base: kubectl apply -k base
13.) check deployment status:
kubectl -n awx logs -f deployments/awx-operator-controller-manager
14.) when script completes check:
kubectl -n awx get awx, all, ingress, secret
15.) logon: https: //temp-awx.maddog.local

```