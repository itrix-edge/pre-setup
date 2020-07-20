pre-setup: Setup scripts for L4T compute nodes
==============================================

This helper ansible scripts are used to change configuration on L4T target boards, make it easier to install application orchestration software on it.


## Contents

### docker-postinstall
Apply specified docker settings for nvidia-docker runtime and kubernetes.

### enabme-mDNS
Enable local compute node DNS probe.

### init-nvme
Initialize NVMe device as external docker data-folder.

### kubernetes-setup
Change L4T hardware settings for kubernetes installation requirement.

### siwtch-text-mode
Change compute node running on text mode as default.

## How to use

pre-setup is an ansible project, run it with ansible playbook works.

To manage nodes with ansible, all clinets should setup SSH key login access with same user account and sudo password. Please refer ansible document for detail steps.

1. Copy `inventory.sample` to the new file `inventory`, modify file contains according your playform setting.
2. Run ansible playbook to start the deployment:

   ```=shell
    $ ansible-playbook -i inventory
   ```
### Update kernel

This playbook accept kernel image `update-kernel.tbz2` for update kernel tasks. If file `update-kernel.tbz2` exist on pre-setup directory root, it will automatic apply to target machine during playbook runs.

After new kernel image is ready, developers can use following command to create file `update-kernel.tbz2`:
```=shell
$ tar cjf update-kernel.tbz2 Image modules
```
where file `Image` are prebuild kernel image and `modules` directory contains kernel modules used by this kernel.