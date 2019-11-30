# virt-create

A simple script that uses the linux `dialog` tool to provide a terminal dialog
sequence for quickly creating KVM libvirt domains. It will prompt for the
following options and attempt to start an unattended install of your VM:

- VM name
- RAM Size (in MB)
- Number of virtual CPUs
- Primary disk size
- Installation media (ISO file, uses `dialog --fselect`)
- User password for unattended install
- Network (enumerates available networks and state from `virsh net-list`
- OS Variant for unattended install (enumerates valid options from
  `osinfo-query`)

It will prompt one last time before creating the VM to ensure you are sure you
want to create the specified VM, and then will begin the installation using
`virt-install`. By default, this will launch `virt-viewer` to view the
installation process. After installation has completed, you can close
`virt-viewer` which will end the script.

You can also bypass the first prompt by passing the intended VM name as the
first parameter to the script (e.g. `virt-create snazzy-domain`).
