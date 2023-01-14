# microk8s

- ubuntu 18.04 beaver

- sudo snap install microk8s --classic --channel=1.18/stable

- sudo ufw allow in on cni0 && sudo ufw allow out on cni0
- sudo ufw default allow routed

- sudo microk8s enable dns dashboard storage


- curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
- sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

- sudo microk8s kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml





