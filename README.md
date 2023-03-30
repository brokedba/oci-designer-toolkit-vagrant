# oci-designer-toolkit-vagrant

# Vagrant / VirtualBox
Prerequisites
- Install Oracle VM VirtualBox
- Install Vagrant
- Create local directory ~/okit/user/templates for storage of custom templates.
# Copy Config & Key Files
Before building/rebuilding your chosen container you will need to copy the contents of <USER HOME DIR>/.oci into /oci directory.

Create Git Repository Properties File & Copy SSH Keys

# Vagrant Build
- MacOS / Linux
cd oci-designer-toolkit/containers/vagrant
vagrant up; vagrant reload; vagrant ssh
- Windows
cd oci-designer-toolkit\containers\vagrant
vagrant up & vagrant reload & vagrant ssh
NOTE: This step takes about 30 minutes on my mac when you build the VM, a little longer the first time as the Vbox image is downloaded from github. Once the VM is built the vagrant up should just take a few seconds.
