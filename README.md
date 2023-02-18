# microshift-ansible-demo

This repository is an Ansible Playbook Demo for installing MicroShift 4.12 on Red Hat Enterprise Linux 8.7.

## Requirements

(local)

- Red Hat Enterprise Linux 8.7

(Remote)

- Red Hat Enterprise Linux 8.7
- SSH connection with password authentication

## Instructions

### 1. Install ansible and sshpass in the local environment

```bash
(local) $ sudo dnf install -y ansible sshpass
(local) $ ansible-galaxy collection install community.general
```

### 2. Clone the repository in the local environment

```bash
(local) $ cd ~/
(local) $ git clone https://github.com/m0ch1m0ch1/microshift-ansible-demo/
```

### 3. Change parameters for accessing the remote environment

Set IP address and username in hosts file.

```bash
(local) $ cd ~/microshift-ansible-demo
(local) $ vim hosts
[remote]
0.0.0.0                 <= set IP address

[remote:vars]
ansible_user=hogehoge   <= set username
```

### 4. Get&Place pull secret

Download your pull secret from the [Red Hat Hybrid Cloud Console](https://console.redhat.com/).
Place pull secret in the `files` folder with the name `openshift-pull-secret`. (.txt extension is not required.)

```bash
(local) $ ls ~/microshift-ansible-demo/files
openshift-pull-secret
```

### 5. Run the playbook

```bash
(local) $ cd ./microshift-ansible-demo
(local) $ ansible-playbook playbook.yml -i hosts --ask-become-pass --ask-pass
```
