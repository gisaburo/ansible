ansible-playbook -i inventory .yml --ask-become-pass --tags "setup" --check 
ansible-playbook -i localhost, -c local local.yml --ask-become-pass --tags "setup"
ansible-playbook -i localhost, -c local local.yml --ask-become-pass --tags "storage"
ansible-playbook -i localhost, -c local local.yml --ask-become-pass --tags "network"
ansible-playbook -i localhost, -c local local.yml --ask-become-pass --tags "guest"
ansible-playbook -i inventory/hosts local.yml --ask-become-pass --tags "guest"
ansible-playbook -i inventory kvm.yml --ask-become-pass --tags "network" --check
ansible-playbook -i inventory kvm.yml --ask-become-pass --tags "storage" --check
ansible-playbook -i inventory kvm.yml --ask-become-pass --tags "guest"

ansible-playbook -i inventory/hosts site.yml --ask-become-pass
ansible-playbook -i inventory/hosts qcow.yml --ask-become-pass
ansible-playbook -i inventory/hosts k8s.yml --ask-become-pass
ansible-playbook -i inventory/hosts kvm_cloud_k8s_singleplane.yml
ansible-playbook -i inventory/hosts kvm_cloud_k8s_nfs.yml
sudo dnf install libguestfs-tools-c
ansible-inventory -i inventory01.ini --graph