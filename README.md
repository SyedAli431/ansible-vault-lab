**Ansible Vault Lab Assignment**

**Objective**

This lab is made to understand how the feature Ansible Vault works in securing senestive data within Ansible playbooks such 
as passwords, API Keys, and SSH keys. This lab will go over the general configuration setup along wtih seeing how Ansible playbooks
interact with the Ansbile Vault. Additionally, it will show how to setup Ansible Vaults for multiple environment including prod and dev.


**Repository Setup**

1) Create a new GitHub repository called "ansible-vault-lab":
   
  GitHub > Repositories > New > Create repositroy

2) Create a PAT token so that all files and directories can be commited to repo later:

   Click Profile > Settings > Developer settings > Personal access tokens > Token (classic)

   **NOTE**: Enusre that you copy the PAT key and save it somewhere as this is the only time the value can be viewed

4) Clone the repository to local machine to begin configuration:

  git clone https://github.com/<github-username>/ansible-vault-lab.git

4) The following directory structure is created for this lab:

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


**Ansible Vault Basic Operations**

1) A encrypted file will be created which is used to store the senesetive data that should not be put in plain-text. This
Can be done by using the command (Ensure you are in root directory of repository for this)

ansible-vault create group_vars/all/vault.yml

2) Inside of this encrypted vault.yml file, the following data is included:

vault_user_password: "secure_password123"

vault_api_key: "api_key_123456"

vault_db_credentials:

  username: "db_admin"
  
  password: "db_pass_123"

Each variable defined in the file stores a different credential and will be used in Ansible playbooks later

Since the vault.yml file in encrypted, the contents of the file cannot be easily viewed using a cat command:

$ANSIBLE_VAULT;1.2;AES256;common
34636335656638393930613038343933353235373966396665363665373562656130336232616261
3966633130356462653661313262316538353234326130330a303938363563323162363764623137
35323631366231363762613365393366333532313135323966316431333239653537366665323265
3164616337343133610a373934366635353764666530663431653635373934373965616362626362
64313966303562346239646138376163373330623061393634333535663064616237366437313462
36663739386430303038656339356566623238366337623934646631356166666334376332616639
61346439356135303133643936363039653963653638373063623534316364353163663033346165
37626630653765343365326530643133373034356539363738326133343639633235363266646437
31646535313534653236623034643137656231393466323132383566623132383463656237653037
31363333336262633535663534323833633663633264343336323763313166643434326563333536
38333066373632323261613765303832633133656131636538323539633831613930663061363565
65323331343035386237


3) To be able to use the credentials stored in the vault.yml file in Ansible playbooks, another file being vars.yml needs to be created which acts a reference to the variables defined in the vault.yml file. The encrypted credentials can then be used.






















