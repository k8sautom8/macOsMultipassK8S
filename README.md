**README.md**

---


# 🚀 macOS Multipass Kubernetes Setup  

An **Ansible playbook** to set up a **Kubernetes cluster on macOS** using **Multipass** for VM management. Ideal for **Mac Mini M4** or any macOS system!  

## 📌 Prerequisites  

### 1️⃣ Install **Multipass**  
Multipass allows you to create and manage lightweight Ubuntu VMs on macOS.  

🔗 **Download:** [Multipass for macOS](https://canonical.com/multipass/download/macos)  
📖 **Setup Guide:** [Multipass Docs](https://canonical.com/multipass/docs/install-multipass)  

### 2️⃣ Install **Homebrew**  
Homebrew is the missing package manager for macOS.  

📖 **Install it using:**  
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

🔗 [Homebrew Website](https://brew.sh/)  

### 3️⃣ Install **Ansible**  
Once Homebrew is installed, install Ansible with:  
```sh
brew update  
brew install ansible  
```

---

## 🚀 How to Run the Playbook  

Once all prerequisites are installed, clone this repository and run the playbook:  


```sh
git clone https://github.com/k8sautom8/macOsMultipassK8S.git
cd macOsMultipassK8S
```

**Please edit playbook vars section -> network: en1 and replace with you own interface name, en1=wifi in my case see below,**

```% multipass networks
Name   Type       Description
en0    ethernet   Ethernet
en1    wifi       Wi-Fi
en5    ethernet   Ethernet Adapter (en5)
en6    ethernet   Ethernet Adapter (en6)
en7    ethernet   Ethernet Adapter (en7)
```
**Execute Playbook**
```
/opt/homebrew/bin/ansible-playbook multipass-standup.yaml
```

This will automatically:  
✅ Create and configure **Multipass VMs** (Master + Workers)  
✅ Install **Kubernetes** (Kubeadm, Kubelet, Kubectl)  
✅ Configure **networking** and **Calico CNI**  
✅ Set up **kubectl** access on the master node  

---

## 🛠️ Manually Managing Multipass VMs  

🔹 **List all VMs:**  
```sh
multipass list
```
🔹 **Stop a VM:**  
```sh
multipass stop <vm-name>
```
🔹 **Start a VM:**  
```sh
multipass start <vm-name>
```
🔹 **Delete a VM:**  
```sh
multipass delete <vm-name> && multipass purge
```

---

## ❓ Troubleshooting  

🔹 **If Multipass VMs are not starting, restart the Multipass service:**  
```sh
multipass stop --all && multipass start --all
```
🔹 **If Ansible fails due to missing dependencies, rerun:**  
```sh
brew update && brew reinstall ansible
```
🔹 **If Kubernetes pods are not coming up, check logs:**  
```sh
kubectl get pods -A
```

---

## 📌 Contributing  
Feel free to open issues, submit pull requests, or suggest improvements! 🚀  

## 📄 License  
This project is licensed under the **MIT License**.  

---

💡 **Enjoy your Kubernetes cluster on macOS!** 🚀🎉  
```
