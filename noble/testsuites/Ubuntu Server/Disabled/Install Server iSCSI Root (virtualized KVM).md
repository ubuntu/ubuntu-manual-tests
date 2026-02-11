Scope of this testcase is to install an iSCSI server on KVM **Prerequisites**

Make sure that your processor supports hardware virtualization running in terminal: `egrep ""flags.*:.*(svm|vmx)"" /proc/cpuinfo`
   If it prints anything the processor is suitable to use KVM

sudo apt-get install qemu-kvm virt-manager
Open Virtual Manager and connect to localhost. We will be using the default network for the first part of the environment set up, which allows DHCP and forwarding, as we will need Internet connection

**If all actions produce the expected results listed, please submit a 'passed' result. If an action fails, or produces an unexpected result, please submit a 'failed' result and file a bug. Please be sure to include the bug number when you submit your result.**