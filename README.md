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

```bash
tar -xvf gost-server-ubuntu.ova
```

##  Prepare for Upload (Install Google Cloud SDK)

The good news is that the Google Cloud command-line tool can now handle the processing and uploading of your `.ova` file in a single step.

Before we can upload, you need the **Google Cloud SDK (`gcloud`)** installed and configured on the computer where you saved the `.ova` file.

#### **1. Install the Google Cloud SDK**

If you don't already have it, follow the official instructions to install the SDK on your operating system (Windows, macOS, or Linux).

  * **Official Install Guide:** [https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)

#### **2. Initialize the SDK**

Once installed, open a new terminal or command prompt and run this command. It will walk you through authenticating your account and selecting the GCP project you want to work with.

```bash
gcloud init
```

  * This command will open a web browser, asking you to log in to your Google account.
  * After logging in, it will ask you to choose the cloud project where you want to upload your image. **Select the project your team will use.**

This one-time setup configures the SDK to work with your account.

## Upload

```bash
gcloud config set compute/region europe-west4
```
```bash
gcloud storage buckets create gs://gost-server-image-files
```
```bash
gcloud storage cp gost-server-ubuntu-disk1.vmdk gs://gost-server-image-files
```
```bash
gcloud migration vms image-imports create gostserver-import-1 --source-file=gs://gost-server-image-files/gost-server-ubuntu.ova
```

Excellent, the import job is now running in the cloud. Here are the final steps to monitor the process and share the finished image with your team.

-----

## Monitor the Import Job

The import process can take some time. Check its status from the command line.

1.  Run the `describe` command to see the current state of the import job. Use the same region you specified when creating the job.

    ```bash
    # Use the same region you used before
    gcloud migration vms image-imports describe gostserver-import-1 --region=europe-west4
    ```

    Look for the `state` field in the output. It will eventually change to `state: SUCCEEDED`.

2.  Alternatively, it can be monitor in the web console by navigating to **VM Migration \> Image Imports**.

##Verify the New Image

Once the job succeeds, the custom image will be ready.

  * In the GCP console, go to **Compute Engine \> Images**.
  * New image listed, likely with a name derived from the `.ova` file, such as `gostserver-ubuntu`.

-----

## Enable the service

1. Log in to the Google Cloud console at console.cloud.google.com.
2. At the very top of the page, you will see a search bar that says "Search products and resources".
3. Type Migrate to Virtual Machines into that search bar.
4. Click on the result that appears.

This will take to the correct page where you will see the button to Enable or Start Setup. Pick the right project.
On the dashboard page:
1. Find the box titled Add targets.
2. Click the blue button inside that box labeled MANAGE TARGETS.

After clicking it, a new page may load. Need to click another "Add" or "Create" button to confirm. Not need to fill out any complex forms. 

```bash
gcloud storage buckets add-iam-policy-binding gs://gost-server-image-files --member=serviceAccount:service-XXXXXXXXXXX@gcp-sa-vmmigration.iam.gserviceaccount.com --role=roles/storage.objectViewer
gcloud migration vms image-imports create gostserver-import-1 --source-file=gs://gost-server-image-files/gost-server-ubuntu-disk1.vmdk
```

Then go to ``Migrate to Virtual Machines > Image Imports`` to see the state of the importation. 
When the importation is done (process can take up to 30 minutes) run
```bash
gcloud migration vms image-imports describe gostserver-import-1 --region=us-central1
```

Wait until see state: ``SUCCEEDED``

## Share the Image 


1.  Stay on the **Compute Engine \> Images** page.
2.  Find the new image in the list and check the box next to it.
3.  On the right side of the screen, a permissions panel will appear. Click **Add Principal**.
4.  In the **New principals** field, enter the email addresses . (For easier management, you can create a Google Group and add the group's email address).
5.  In the **Select a role** dropdown, find and choose **`Compute Engine > Compute Image User`**.
6.  Click **Save**.



**Final Reminder:** Run the following commands the very first time they launch a VM from this image to install the GCP guest tools:

```bash
sudo apt update -y
```
```bash
sudo apt install -y google-guest-agent google-osconfig-agent
```
