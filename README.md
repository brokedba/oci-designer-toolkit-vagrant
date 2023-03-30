# oci-designer-toolkit-vagrant
![image](https://user-images.githubusercontent.com/29458929/228986963-98e3e65e-d66a-4f7a-888a-bc4c1a5526cd.png)
![image](https://user-images.githubusercontent.com/29458929/228987071-f1d46885-fa8a-4c3e-a4fa-ed0a3fc6a72b.png)

# Vagrant / VirtualBox
Prerequisites
- Install Oracle VM VirtualBox
- Install Vagrant
- Create local directory ~/okit/user/templates for storage of custom templates.
# Copy Config & Key Files
Before building/rebuilding your chosen container you will need to copy the contents of <USER HOME DIR>/.oci into /oci directory.
Create / Generate Connection Information
If you already have the OCI sdk/cli installed on you machine you can use the previously generated pem key and config file we will assume that this exists in <USER HOME DIR>/.oci

- Key File
If you do not have a previously generated private key you will need to create a private/public key pair for use with OKIT and OCI. These keys can be generated using the following commands as defined in Required Keys and OCIDs.
```
openssl genrsa -out <USER HOME DIR>/.oci/oci_api_key.pem 2048   
openssl rsa -pubout -in <USER HOME DIR>/.oci/oci_api_key.pem -out <USER HOME DIR>/.oci/oci_api_key_public.pem                                  
```
  Upload the generated oci_api_key_public.pem to OCI through the console and record the associated fingerprint following upload.

- Get Fingerprint
```
  openssl rsa -pubout -outform DER -in ~/.oci/oci_api_key.pem | openssl md5 -c
```
# OCI Config File
Create the OCI cli config file in the directory <USER HOME DIR>/.oci with contents similar to that below. The key_file is a fixed value because the contents of the <USER HOME DIR>/.oci will be mounted to the appropriate users home directory, as ~/.oci, during the run process.
```
[DEFAULT]
user=ocid1.user.oc1..aaaaaaaak6z......
fingerprint=3b:7e:37:ec:a0:86:1....
key_file=~/.oci/oci_api_key.pem  
tenancy=ocid1.tenancy.oc1..aaaaaaaawpqblfem........
region=us-phoenix-1
```
 # GIT Settings File
If Git integration is required you will need to create a git_repositories file within the directory <USER HOME DIR>/.oci with contents similar to that below.
```
[OKIT Community Templates]
branch=main
url=git@github.com:sbemarkar/okit-templates.git

[Example Repo]
branch = master
url = git@https://github.com/brokedba/terraform-examples.git

[Internal]
branch = BRANCHNAME
url = git@url2.git
```
This properties file contains a list of the Git repositories you want to access. It assumes that you are using public/private key access, the key files exist within your <USER HOME DIR>/.ssh directory and the <USER HOME DIR>/.ssh/config defines the key/url mapping, similar to the following.

Host github.com
	IdentityFile ~/.ssh/id_rsa_github

Create Git Repository Properties File & Copy SSH Keys

# Vagrant Build
- MacOS / Linux
```
  cd oci-designer-toolkit-vagrant/
vagrant up; vagrant reload; vagrant ssh
```
  - Windows
cd oci-designer-toolkit-vagrant\
```
  vagrant up & vagrant reload & vagrant ssh
```
- Once the Vbox image and the VM built, you can then hit the browser 
  http://localhost:8080/okit/designer.
