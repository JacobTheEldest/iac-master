# Setup an iac-master 

## Use the `initial_setup.sh` script to pull this github repository
```
wget -q -O - https://raw.githubusercontent.com/JacobTheEldest/iac-master/master/initial_setup.sh | bash
```

## decrypt the necessary files with `decrypt.sh`
```
./decrypt.sh
```

## Place the ssh files with the appropriate script in the `sensitive` directory
```
sensitive/place_ssh_files.sh
```

## Install ansible and install the requirements
```
install_ansible.sh
ansible-galaxy install -r ansible/requirements.yaml
```

## Run the ansible playbook to setup iac-master
Set `restore` to true to restore from the most recent backup

Set `backup` to true to enable backups for this host

```
ansible-playbook ansible/iac-master.yml -i ansible/inventory/iac-master -e "restore=true backup=false"
```
