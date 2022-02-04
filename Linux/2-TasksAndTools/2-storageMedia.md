# Managing storage media

## mount - Mount a file system
- The process of attaching a storage device to the file system tree is called mounting.
- Usage: `mount <device> <mountPoint>`
- A file named `/etc/fstab` (short for file system table) lists the devices that are to be mounted at boot time.
- View a list of mounted file systems: `mount`
- Use the `-t` flag to specify the file system type.
- Examples:
  - `mount`
  - `mount /dev/sdb1 /mnt/myUSB`
  - `mount -t iso9660 /dev/sdc /mnt/cdrom`

## umount - Umount a file system
- The process of detaching the storage media from the file system tree is called unmounting.
- Usage: `umount <device>`
- Always remember to umount your devices because, unmounting a device entails writing all the remaining data to the device so that it can be safely removed.
- Example:
  - `umount /dev/sdb1`

## Check all devices
- You can check all the devices by listing the `/dev` directory.

## TIP
- Using the `tail -f /var/log/messages` technique is a great way to watch what the system is doing in near real-time.

## fdisk - Manipulate disk partition table
- fdisk allows us to interact directly with disk-like devices at a very low level.
- Usage: `fdisk [arguments] [device]`
- To view all devices: `sudo fdisk -l`
- Unmount your device before working on it with fdisk.
- To see a list of the available partition types use `l` command after entering fdisk interactive mode.
- To change a partition's system id use `t` command in interactive mode.
- To write the changes use `w` command in interactive mode.
- Examples:
  - `sudo fdisk /dev/sdb`

## mkfs - Create a file system
- mkfs is short for make file system, it can create file systems in a variety of formats.
- Usage: `mkfs [arguments] [device]`
- Use the `-t` flag to specify system type.
- Examples:
  - `sudo mkfs -t ext4 /dev/sdb1`
  - `sudo mkfs -t vfat /dev/sdb1`

## fsck - Check and repair system
- It stands for "file system check" and is used to check the integrity of file systems and repair corrupt file systems.
- Usage: `sudo fsck [arguments] [device]`
- Example:
  - `sudo fsck /dev/sdb1`

## dd - Convert and copy a file
- It copies blocks of data from one place to another. So it can be used to clone devices.
- Usage: `dd if=<input_file> of=<output_file> [bs=<block_size> [count=<blocks>]]`
- Example:
  - `dd if=/dev/sdb1 of=/home/carlos/flashDrive.iso`

## genisoimage (mkisofs) - Create an ISO 9660 image file
- To create an ISO image file containing the contents of a directory, we use the genisoimage program.
- Usage: `genisoimage -o <outputFile> -R -J <directory>`
- Example:
  - `genisoimage -o cd-rom.iso -R -J ~/cd-rom-files`

## wodim (cdrecord) - Write data to optical storage media
- Blank out a CD-RW device: `wodim dev=/dev/cdrw blank=fast`
- Write an image into it: `wodim dev=/dev/cdrw image.iso`

## md5sum - Calculate an MD5 checksum
- Used to calculate the MD5 checksum of a file.
- Usage: `md5sum <file>`
- Examples: `md5sum secretFile.txt`

## df - disk free
- It is used to check the total and available space.
- Usage: `df [options]`
- Use the `-h` flag to view the space in human readable format.
- Example:
  - `df`
  - `df -h`