ansible-playbook microk8splaybook.yml --ask-become-pass
...
BECOME password:

microk8s enable storage dns ingress

git clone https://github.com/ansible/awx-operator.git
cd awx-operator

git checkout 0.30.0
export NAMESPACE=ansible-awx
sudo apt install make
make deploy

awx resource:
kubectl apply -f my-awx.yml -n ansible-awx

ingress settings:
kubectl apply -f my-awx-ingress.yml -n ansible-awx

Once a settings is applied we have opportunity to access AWX by 80 port.

The default username is admin. The password randomly generated. For this we need to do following command:

kubectl get secret awx-demo-admin-password -n ansible-awx -o jsonpath='{.data.password}' | base64 --decode


