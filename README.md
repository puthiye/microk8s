# microk8s

- ubuntu 18.04 beaver

- For raspberry pi
  - use this version - sudo snap install microk8s --classic --channel=1.27
  - append these control groups - cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory in /boot/firmware/cmdline.txt
  - sudo apt install linux-modules-extra-raspi
  - reboot
  
- sudo snap install microk8s --classic --channel=1.18/stable

- sudo ufw allow in on cni0 && sudo ufw allow out on cni0
- sudo ufw default allow routed

- sudo microk8s enable dns dashboard storage


- curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
- sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

- sudo microk8s kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml

Refer - https://ubuntu.com/tutorials/install-a-local-kubernetes-with-microk8s#4-accessing-the-kubernetes-dashboard

**TIPS**

If you would like to skip user login/token auth for dashboard, follow the below steps

- sudo microk8s.kubectl -n kube-system edit deploy kubernetes-dashboard -o yaml 

Add the –enable-skip-login flag to the deployment’s specs:

    spec:
      containers:
      - args:
        - --auto-generate-certificates
        - --namespace=kube-system
        - --enable-skip-login

**Troubleshooting**

1. k8s pods running are not logging any print() logs. Fix is to add ENV PYTHONUNBUFFERED 1 in Dockerfile or update the container image with below code
        env:
         - name: PYTHONUNBUFFERED
           value: "1"

**Remove snap microk8s**
- sudo microk8s reset
- sudo snap remove microk8s
