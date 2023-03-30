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
