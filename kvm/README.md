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
ansible-playbook -i inventory/hosts kvm_cloud_k8s_singleplane.yml --ask-become-pass
sudo dnf install libguestfs-tools-c
