# C2 image for GCP instance

## VM Machine setup

- ubuntu-24.04.2-live-server-amd64 (minimal installation)
- 4GB RAM
- 100 GB Disk
- 2 CPU cores
- English 
- English (US)
- OpenSSH server installed by default (temporary allow pass auth)

## Installing

```bash
whoami
```
    
```bash
groups
```
    
```bash
sudo whoami
```
    
```bash
sudo apt update -y
```
    
```bash
sudo apt upgrade -y
```

```bash
sudo apt install -y build-essential autoconf automake libtool pkg-config libssl-dev libpcap-dev libreadline-dev zlib1g-dev git curl wget ca-certificates unzip screen python3-pip python3-venv python3-dev ruby-full cmake ninja-build meson net-tools iputils-ping dnsutils tcpdump libsasl2-dev libldap2-dev gnupg2 vim nano
```
    
```bash
sudo groupadd gosteam
sudo usermod -aG gosteam gost
sudo mkdir -p /opt/tools
sudo chown -R root:gosteam /opt/tools
sudo chmod -R 775 /opt/tools
echo 'export PATH=$PATH:/opt/tools' | sudo tee /etc/profile.d/gosteam.sh
sudo reboot
```
    
```bash
wget https://go.dev/dl/go1.23.5.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.23.5.linux-amd64.tar.gz
rm -rf go1.23.5.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' | sudo tee /etc/profile.d/go.sh
sudo reboot
```
    
```bash
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker gost
sudo reboot
```
    
```bash
sudo mkdir -p /opt/rust
sudo chown -R gost:gosteam /opt/rust
export RUSTUP_HOME=/opt/rust
export CARGO_HOME=/opt/rust
curl https://sh.rustup.rs -sSf | sh -s -- -y
sudo apt install -y libclang-dev clang libkrb5-dev
sudo nano  /etc/profile.d/custom-rust.sh
```
    
```bash
# inside the custom-rust.sh
    
export RUSTUP_HOME=/opt/rust
export CARGO_HOME=/opt/rust
export PATH=/opt/rust/bin:$PATH
export LIBCLANG_PATH=/usr/lib/llvm-18/lib
export LD_LIBRARY_PATH=/usr/lib/llvm-18/lib:$LD_LIBRARY_PATH
```

```bash
sudo reboot
```
    
```bash
sudo apt install -y smbmap whatweb apache2 proxychains4 sendemail plocate
sudo snap install sqlmap enum4linux
```

```bash
docker pull blacklantersecurity/manspider
docker run blacklanternsecurity/manspider --help
```
```bash
docker pull leonjza/gowitness
docker run --rm leonjza/gowitness gowitness
```

```bash
sudo apt install -y alien
wget https://nmap.org/dist/nmap-7.97-1.x86_64.rpm
sudo alien nmap-7.97-1.x86_64.rpm
sudo dpkg --install nmap_7.97-2_amd64.deb
rm -rf nmap*
```

```bash
sudo apt install -y pip x
pipx ensurepath
pipx completions
eval "$(register-python-argcomplete pipx)"
sudo reboot
pipx install git+https://github.com/AetherBlack/abuseACL/
pipx install git+https://github.com/CravateRouge/bloodyAD
pipx install git+https://github.com/ly4k/Certipy
pipx install impacket
pipx install git+https://github.com/dirkjanm/adidnsdump
pipx install git+https://github.com/Pennyw0rth/NetExec 
```

```bash
cd /opt/gostools
python3 -m venv env
source env/bin/activate
```

```bash
git clone https://github.com/iphelix/dnschef.git 
cd dnschef
pip install -r requirements.txt
cd ..

git clone https://github.com/GoSecure/ldap-scanner.git
pip install impacket
```
```bash
mkdir gmapsapiscanner
cd gmapsapiscanner
wget https://raw.githubusercontent.com/ozguralp/gmapsapiscanner/refs/heads/master/maps_api_scanner.py
cd ..
```
```bash
git clone https://github.com/VitoBonetti/ADenum.git 
cd ADenum
pip install -r requirements.txt
cd ..
```
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs

git clone https://github.com/dirkjanm/roadtools.git
cd roadtools
pip install -e roadlib/
pip install -e roadrecon/
cd roadrecon/frontend/
npm install
cd /opt/gostools
```

```bash
git clone https://github.com/NH-RED-TEAM/RustHound
cd RustHound
make install
rusthound -h
cd ..
```
```bash
git clone https://github.com/g0h4n/RustHound-CE.git
cd RustHound-CE
make release
rusthound-ce -h
cd ..
```

```bash
go install mvdan.cc/garble@master
```
```bash
git clone https://github.com/0x00-0x00/ligolo-ng
cd ligolo-ng
go build -o lg-proxy cmd/proxy/main.go
sudo ln -s /opt/gostools/ligolo-ng/lg-proxy /usr/bin/lg-proxy
cd ..
```

```bash
git clone https://github.com/danielmiessler/SecLists.git
```

```bash
pip install pyOpenSSL lxml setuptools
```

```bash
mkdir inflator
cd inflator
wget https://raw.githubusercontent.com/VB01070/inflate/refs/heads/main/inflator.py
cd ..
```
```bash
git clone https://github.com/dirkjanm/krbrelayx.git
```
```bash
git clone https://github.com/SecuraBV/Timeroast.git
```
```bash
git clone https://github.com/ShutdownRepo/targetedKerberoast.git
```
```bash
git clone https://github.com/hashcat/hashcat.git
cd hashcat
make
sudo ln -s /opt/gostools/hashcat/hashcat /usr/bin/hashcat
cd ..
```
```bash
git clone https://github.com/Macmod/godap
cd godap
go install .
echo 'cd /opt/gostools/godap' | tee godap.sh
echo 'go run .' | tee -a godap.sh
chmod +x godap.sh
sudo ln -s /opt/gostools/godap/godap.sh /usr/bin/godap
```
```bash
curl https://sliver.sh/install|sudo bash
```
```bash
sudo npm install -g @google/gemini-cli
```
```bash
sudo apt install -y snmp samba-client
```
```bash
wget https://github.com/ffuf/ffuf/releases/download/v2.1.0/ffuf_2.1.0_linux_amd64.tar.gz
tar -xzf ffuf_2.1.0_linux_amd64.tar.gz
rm LICENSE
rm *.md
```

```bash
nano gost-servr
```

```bash
#!/bin/bash

cat << "EOF"
                 _                                       
                | |                                      
  __ _  ___  ___| |_ ______ ___  ___ _ ____     _____ _ __ 
 / _` |/ _ \/ __| __|______/ __|/ _ \ '__\ \ / / _ \ '__|
| (_| | (_) \__ \ |_        \__ \ __/ |   \ V /  __/ |   
 \__, |\___/|___/\__|      |___/\___|_|    \_/ \___|_|   
  __/ |                                                  
 |___/                                                   

|---------------|---------------|---------------|---------------|
| pipx          | docker        | apt & snap    | tunnel        |
|---------------|---------------|---------------|---------------|
| abuseACL      | gowitness     | smbmap        | ligolo        |
| bloodyAD      | manspider     | whatweb       | sliver        |
| Certipy       |               | apache2       | redraptor-c2  |
| impacket      |               | proxychains4  | go-socks5     |
| adidnsdump    |               | sendemail     |               |
| NetExec       |               | sqlmap        |               |
|               |               | enum4linux    |               |
|---------------|---------------|---------------|---------------|
|                                                               |
| - python venv: /opt/gostools/                                 |
| - SecList: /opt/gostools/SecList                              |
| - Other Tools: /opt/gostools                                  |
| - gemini-cli is installed but not configured                  |
|     visit: https://github.com/google-gemini/gemini-cli        |
| - mc_pentesting_server installed but not configured           |
|                                                               |
|                                                               |
| All the tools installe with `pipx` do NOT                     |
| need virtual env to be activate.                              |
|                                                               |
| Run docker tool :                                             |
|                                                               |
| docker run --rm leonjza/gowitness gowitness                   |
| docker run blacklanternsecurity/manspider                     |
|                                                               |
|                                                               |
| All the tunnels need to be configured                         |
|                                                               |
| go-nmap command available.                                    |
|                                                               |
| To see this message again run the command:                    |
| gost-server                                                   |
|                                                               |
|---------------------------------------------------------------|
EOF
```

```bash
sudo chmod +x gost-server
```

*Take a snapshot at this point*

## Cleaning up

```bash
sudo apt autoremove --purge -y
sudo apt clean
sudo rm -f /etc/machine-id
sudo touch /etc/machine-id
sudo rm -rf /tmp/* /var/tmp/*
sudo passwd root
history -c && history -w
logout
```
*Login has root*

```bash
sudo userdel -r gost
dd if=/dev/zero of=/EMPTY bs=1M || echo "dd exit code $? is expected"
rm -f /EMPTY
shutdown -h now
```

Excellent. We're now at the final stage. Step 4 involves getting the image out of VMware and into your Google Cloud Platform project.

We'll do this part by part, as you requested.

***

## Export the Image from VMware

The goal here is to get the virtual disk out of VMware in a portable format. The best format for this is an **OVA (Open Virtualization Appliance)** file, which packages your entire VM into a single, convenient file.

#### **1. Check for Snapshots (Crucial Prerequisite)**

Before to export,  **ensure  VM has no snapshots**.

* In VMware, select  VM.
* Go to `VM > Snapshot > Snapshot Manager`.
* If any snapshots exist, **delete them**. This will consolidate all changes into the main virtual disk file. This process can take a few minutes.

#### **2. Export to an OVA File**

With the VM **powered off** and **no snapshots**, you can now export it.

* In VMware Workstation, select the  VM from the library.
* From the top menu bar, click **`File > Export to OVF...`**.
* A save dialog will appear. Give file a name (e.g., `gost-server-ubuntu.ova`).
* In the "Format" or "Save as type" dropdown, choose **OVA (.ova)**.
* Save the file.

VMware will package th VM into a single `.ova` file. This process might take several minutes, depending on the size of your VM's disk.

***
