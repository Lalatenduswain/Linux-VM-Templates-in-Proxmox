# Linux-VM-Templates-in-Proxmox

The script is designed to fetch a variety of preconfigured cloud images from the popular Linux distributions and install them as fresh VM templates with 900-numbered IDs, along with the configuration of my preference and the inclusion of your SSH keys. Before executing the script, you may customise the settings as per your needs and specify your username after saving your public key in a text file.

This script is used to create virtual machine templates in Proxmox. It automates the process of setting up and configuring a new virtual machine with predefined settings.

### Usage

To use this script, follow the steps below:

1. Set the required variables at the beginning of the script:
   - `ssh_keyfile`: Path to your SSH authorized_keys file or `/etc/pve/priv/authorized_keys` if you are already authorized on the Proxmox system.
   - `username`: Username to create on the VM template.
   - `storage`: Name of your storage.

2. The script creates templates for various operating systems. You can customize the templates or add your own. Here are some examples provided in the script:

   - Ubuntu 22.04 (Jammy Jellyfish)
   - Ubuntu 23.04 (Lunar Lobster) - daily builds
   - Fedora 37
   - CentOS Stream 8
   - CentOS Stream 9 (daily)
   - Rocky Linux (Stream 8)

3. Run the script using the following command:
```
bash ProxMoxVMTamplet.sh
   ```
Or

   ```
wget https://raw.githubusercontent.com/Lalatenduswain/Linux-VM-Templates-in-Proxmox/master/ProxMoxVMTamplet.sh -O ProxMoxVMTamplet.sh && bash ProxMoxVMTamplet.sh
   ```

### Function: create_template

This function is responsible for creating a template for a specific virtual machine.

#### Arguments

- `vm_id`: The ID of the virtual machine.
- `vm_name`: The name of the virtual machine.
- `file name`: The file name in the current directory.

#### Steps

The function performs the following steps:

1. Prints the configuration information.
2. Creates a new virtual machine with the specified ID, name, and operating system type.
3. Sets the networking to the default bridge.
4. Sets the display to serial.
5. Sets memory, CPU, and type defaults.
6. Sets the boot device to the new file.
7. Sets the SCSI hardware as the default boot disk using virtio SCSI single.
8. Enables QEMU guest agent.
9. Adds cloud-init device.
10. Sets the CI IP configuration.
11. Imports the SSH keyfile.
12. Adds the specified user.
13. Resizes the disk to 8GB.
14. Converts the virtual machine to a template.
15. Removes the file when done.

Note: The script includes additional steps and template creation for different operating systems as per the provided examples.

Feel free to modify the script and add more templates as needed.

**Note:** Make sure to have the necessary permissions and dependencies set up before running this script.

### Donations

If you want to show your appreciation, you can donate via [Buy Me a Coffee](https://www.buymeacoffee.com/lalatendu.swain)

## Disclaimer

This script is provided as-is and may require modifications or updates based on your specific environment and requirements. Use it at your own risk. The authors of the script are not liable for any damages or issues caused by its usage.
