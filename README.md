**Ansible Vault Lab Assignment**

**Objective**

This lab is made to understand how the feature Ansible Vault works in securing senestive data within Ansible playbooks such 
as passwords, API Keys, and SSH keys. This lab will go over the general configuration setup along wtih seeing how Ansible playbooks
interact with the Ansbile Vault. Additionally, it will show how to setup Ansible Vaults for multiple environment including prod and dev.


**Repository Setup**

1) Create a new GitHub repository called "ansible-vault-lab":
   
  GitHub > Repositories > New > Create repositroy

2) Clone the repository to local machine to begin configuration:

  git clone https://github.com/<github-username>/ansible-vault-lab.git

3) The following directory structure is created for this lab:

ansible-vault-lab/
├── group_vars/
│   └── all/
│       ├── vault.yml (encrypted)
│       └── vars.yml
├── inventory/
│   └── production.ini
├── playbooks/
│   ├── create_user.yml
│   └── configure_service.yml
├── README.md
└── requirements.txt

Use the following commands to create this structure:

mkdir –p group_vars/all 
touch README.md
touch requirements.txt

mkdir inventory/
cd inventory
touch production.ini

mkdir playbooks/
cd playbooks
touch create_user.yml
touch configure_service.yml
cd ..














