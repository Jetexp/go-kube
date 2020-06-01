<div align="center">
  <h1>Go Kubernetes and Minikube</h1>
  <h5>Draft!</h5>
</div>

## Installation steps

### Install kubectl

- [x] `$ grep -E --color 'vmx|svm' /proc/cpuinfo`
- [x] `$ curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl`
- [x] `$ chmod +x ./kubectl`
- [x] `$ sudo mv ./kubectl /usr/local/bin/kubectl`
- [x] `$ kubectl version --client`

### Install Hypervisor

#### KVM

- [x] `$ sudo apt install cpu-checker && sudo kvm-ok` 
    - [ ] OR `$ grep -E '(vmx|svm)' /proc/cpuinfo`
- [x] `$ sudo kvm-ok`

   **Output:**
   
   ```bash
   INFO: /dev/kvm exists
   KVM acceleration can be used
   ```
- [x] `$ sudo apt install libvirt-clients libvirt-daemon-system qemu-kvm && sudo usermod -a -G libvirt $(whoami) && newgrp libvirt`
- [x] `$ sudo virt-host-validate`

### Install Minikube

- [x] `$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube`
- [x] `$ sudo mkdir -p /usr/local/bin/`
- [x] `$ sudo install minikube /usr/local/bin/`

### Check

- [x] `$ minikube start --vm-driver=<driver_name>`, where `<driver-name>` kvm2 or set one of [list of drivers](https://kubernetes.io/ru/docs/setup/learning-environment/minikube/#%D1%83%D0%BA%D0%B0%D0%B7%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B4%D1%80%D0%B0%D0%B9%D0%B2%D0%B5%D1%80%D0%B0-%D0%B2%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9-%D0%BC%D0%B0%D1%88%D0%B8%D0%BD%D1%8B)
- [x] `$ minikube status`
   
   **Output:**
   
   ```bash
   host: Running
   kubelet: Running
   apiserver: Running
   kubeconfig: Configured
   ```

- [x] `$ minikube stop`

### Clear local state

- [x] `$ minikube start`
- [ ] if previous step with error `machine does not exist`, then run `$ minikube delete`
