PROCESS COMMANDS:
top

<img width="755" height="691" alt="image" src="https://github.com/user-attachments/assets/1a622d0d-2578-4723-8625-f76bd50a4e3a" />

ps

<img width="294" height="102" alt="image" src="https://github.com/user-attachments/assets/759e92c2-eb0f-4846-ad50-3142ce92e108" />

ps -ef

<img width="654" height="516" alt="image" src="https://github.com/user-attachments/assets/ed1bbc25-c41f-44b1-83dd-04c6c6de093a" />

pgrep - search for processes by name and return their process IDs (PIDs)

SERVICE COMMANDS:
systemctl status: systemd controller
<img width="1344" height="387" alt="image" src="https://github.com/user-attachments/assets/456dc39d-2ac4-4df0-a8a3-04a93b844dd9" />

systemctl list-units: is a systemd command used to display the currently loaded (active) units on a system. it lists active units, including:
Services (.service)
Mount points (.mount)
Sockets (.socket)
Targets (.target)
Devices (.device)

root@ip-172-31-13-57:/etc/systemd/system# systemctl list-units
  UNIT                                                                         LOAD   ACTIVE SUB       DESCRIPTION
  proc-sys-fs-binfmt_misc.automount                                            loaded active running   Arbitrary Executable File Formats File System Automount Point
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p1.device      loaded active plugged   Amazon Elastic Block Store cloudimg-rootfs
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p13.device     loaded active plugged   Amazon Elastic Block Store BOOT
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p14.device     loaded active plugged   Amazon Elastic Block Store 14
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1-nvme0n1p15.device     loaded active plugged   Amazon Elastic Block Store UEFI
  sys-devices-pci0000:00-0000:00:04.0-nvme-nvme0-nvme0n1.device                loaded active plugged   Amazon Elastic Block Store
  sys-devices-pci0000:00-0000:00:05.0-net-ens5.device                          loaded active plugged   Elastic Network Adapter (ENA)
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.1-tty-ttyS1.device loaded active plugged   /sys/devices/platform/serial8250/serial8250:0/serial8250:0.1/tty/ttyS1
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.2-tty-ttyS2.device loaded active plugged   /sys/devices/platform/serial8250/serial8250:0/serial8250:0.2/tty/ttyS2
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.3-tty-ttyS3.device loaded active plugged   /sys/devices/platform/serial8250/serial8250:0/serial8250:0.3/tty/ttyS3
  sys-devices-pnp0-00:04-00:04:0-00:04:0.0-tty-ttyS0.device                    loaded active plugged   /sys/devices/pnp0/00:04/00:04:0/00:04:0.0/tty/ttyS0
  sys-devices-virtual-block-loop0.device                                       loaded active plugged   /sys/devices/virtual/block/loop0
  sys-devices-virtual-block-loop1.device                                       loaded active plugged   /sys/devices/virtual/block/loop1
  sys-devices-virtual-block-loop2.device                                       loaded active plugged   /sys/devices/virtual/block/loop2
  sys-devices-virtual-misc-rfkill.device                                       loaded active plugged   /sys/devices/virtual/misc/rfkill
  sys-devices-virtual-tty-ttyprintk.device                                     loaded active plugged   /sys/devices/virtual/tty/ttyprintk
  sys-module-configfs.device                                                   loaded active plugged   /sys/module/configfs
  sys-module-fuse.device                                                       loaded active plugged   /sys/module/fuse
  sys-subsystem-net-devices-ens5.device                                        loaded active plugged   Elastic Network Adapter (ENA)
  -.mount                                                                      loaded active mounted   Root Mount
  boot-efi.mount                                                               loaded active mounted   /boot/efi
  boot.mount                                                                   loaded active mounted   /boot
  dev-hugepages.mount                                                          loaded active mounted   Huge Pages File System
  dev-mqueue.mount                                                             loaded active mounted   POSIX Message Queue File System
  proc-sys-fs-binfmt_misc.mount                                                loaded active mounted   Arbitrary Executable File Formats File System
  run-user-1000.mount                                                          loaded active mounted   /run/user/1000
  snap-amazon\x2dssm\x2dagent-13009.mount                                      loaded active mounted   Mount unit for amazon-ssm-agent, revision 13009
  snap-core22-2411.mount                                                       loaded active mounted   Mount unit for core22, revision 2411
  snap-snapd-26382.mount                                                       loaded active mounted   Mount unit for snapd, revision 26382
  sys-fs-fuse-connections.mount                                                loaded active mounted   FUSE Control File System
  sys-kernel-config.mount                                                      loaded active mounted   Kernel Configuration File System
  sys-kernel-debug.mount                                                       loaded active mounted   Kernel Debug File System
  sys-kernel-tracing.mount                                                     loaded active mounted   Kernel Trace File System
  tmp.mount                                                                    loaded active mounted   Temporary Directory /tmp
  acpid.path                                                                   loaded active running   ACPI Events Check
  systemd-ask-password-console.path                                            loaded active waiting   Dispatch Password Requests to Console Directory Watch
  systemd-ask-password-wall.path                                               loaded active waiting   Forward Password Requests to Wall Directory Watch
  init.scope                                                                   loaded active running   System and Service Manager
  session-1.scope                                                              loaded active running   Session 1 of User ubuntu
  acpid.service                                                                loaded active running   ACPI event daemon
  apparmor.service                                                             loaded active exited    Load AppArmor profiles
  apport.service                                                               loaded active exited    automatic crash report generation
  blk-availability.service                                                     loaded active exited    Availability of block devices
  chrony.service                                                               loaded active running   chrony, an NTP client/server
  cloud-config.service                                                         loaded active exited    Cloud-init: Config Stage
  cloud-final.service                                                          loaded active exited    Cloud-init: Final Stage
  cloud-init-local.service                                                     loaded active exited    Cloud-init: Local Stage (pre-network)
  cloud-init-network.service                                                   loaded active exited    Cloud-init: Network Stage
  console-setup.service                                                        loaded active exited    Set console font and keymap
  cron.service                                                                 loaded active running   Regular background program processing daemon
  dbus.service                                                                 loaded active running   D-Bus System Message Bus
  dracut-shutdown.service                                                      loaded active exited    Restore /run/initramfs on shutdown
  finalrd.service                                                              loaded active exited    Create final runtime dir for shutdown pivot root
  getty@tty1.service                                                           loaded active running   Getty on tty1
  irqbalance.service                                                           loaded active running   irqbalance daemon
  keyboard-setup.service                                                       loaded active exited    Set the console keyboard layout
  kmod-static-nodes.service                                                    loaded active exited    Create List of Static Device Nodes
  ldconfig.service                                                             loaded active exited    Rebuild Dynamic Linker Cache
  lvm2-monitor.service                                                         loaded active exited    Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling
  ModemManager.service                                                         loaded active running   Modem Manager
  multipathd-queueing.service                                                  loaded active exited    Enable queuing for multipath maps
  multipathd.service                                                           loaded active running   Device-Mapper Multipath Device Controller
  netplan-configure.service                                                    loaded active exited    Netplan Backend Configuration
  networkd-dispatcher.service                                                  loaded active running   Dispatcher daemon for systemd-networkd
  plymouth-quit-wait.service                                                   loaded active exited    Hold until boot process finishes up
  plymouth-quit.service                                                        loaded active exited    Terminate Plymouth Boot Screen
  plymouth-read-write.service                                                  loaded active exited    Tell Plymouth To Write Out Runtime Data
  polkit.service                                                               loaded active running   Authorization Manager
  rsyslog.service                                                              loaded active running   System Logging Service
  serial-getty@ttyS0.service                                                   loaded active running   Serial Getty on ttyS0
  setvtrgb.service                                                             loaded active exited    Set console scheme
  snap.amazon-ssm-agent.amazon-ssm-agent.service                               loaded active running   Service for snap application amazon-ssm-agent.amazon-ssm-agent
  snapd.apparmor.service                                                       loaded active exited    Load AppArmor profiles managed internally by snapd
  snapd.seeded.service                                                         loaded active exited    Wait until snapd is fully seeded
  snapd.service                                                                loaded active running   Snap Daemon
  ssh.service                                                                  loaded active running   OpenBSD Secure Shell server
  sysstat.service                                                              loaded active exited    Resets System Activity Logs
  systemd-binfmt.service                                                       loaded active exited    Set Up Additional Binary Formats
  systemd-fsck-root.service                                                    loaded active exited    File System Check on Root Device
  systemd-fsck@dev-disk-by\x2dlabel-BOOT.service                               loaded active exited    File System Check on /dev/disk/by-label/BOOT
  systemd-fsck@dev-disk-by\x2dlabel-UEFI.service                               loaded active exited    File System Check on /dev/disk/by-label/UEFI
  systemd-journal-catalog-update.service                                       loaded active exited    Rebuild Journal Catalog
  systemd-journal-flush.service                                                loaded active exited    Flush Journal to Persistent Storage
  systemd-journald.service                                                     loaded active running   Journal Service
  systemd-logind.service                                                       loaded active running   User Login Management
  systemd-machine-id-commit.service                                            loaded active exited    Save Transient machine-id to Disk
  systemd-modules-load.service                                                 loaded active exited    Load Kernel Modules
  systemd-networkd-persistent-storage.service                                  loaded active exited    Enable Persistent Storage in systemd-networkd
  systemd-networkd-wait-online.service                                         loaded active exited    Wait for Network to be Online
  systemd-networkd.service                                                     loaded active running   Network Management
  systemd-random-seed.service                                                  loaded active exited    Load/Save OS Random Seed
  systemd-remount-fs.service                                                   loaded active exited    Remount Root and Kernel File Systems
  systemd-resolved.service                                                     loaded active running   Network Name Resolution
  systemd-sysctl.service                                                       loaded active exited    Apply Kernel Variables
  systemd-sysusers.service                                                     loaded active exited    Create System Users
  systemd-tmpfiles-setup-dev-early.service                                     loaded active exited    Create Static Device Nodes in /dev gracefully
  systemd-tmpfiles-setup-dev.service                                           loaded active exited    Create Static Device Nodes in /dev
  systemd-tmpfiles-setup.service                                               loaded active exited    Create System Files and Directories
  systemd-udev-load-credentials.service                                        loaded active exited    Load udev Rules from Credentials
  systemd-udev-trigger.service                                                 loaded active exited    Coldplug All udev Devices
  systemd-udevd.service                                                        loaded active running   Rule-based Manager for Device Events and Files
  systemd-update-done.service                                                  loaded active exited    Update is Completed
  systemd-user-sessions.service                                                loaded active exited    Permit User Sessions
  udisks2.service                                                              loaded active running   Disk Manager
  ufw.service                                                                  loaded active exited    Uncomplicated firewall
  unattended-upgrades.service                                                  loaded active running   Unattended Upgrades Shutdown
  user-runtime-dir@1000.service                                                loaded active exited    User Runtime Directory /run/user/1000
  user@1000.service                                                            loaded active running   User Manager for UID 1000
  -.slice                                                                      loaded active active    Root Slice
  system-getty.slice                                                           loaded active active    Slice /system/getty
  system-modprobe.slice                                                        loaded active active    Slice /system/modprobe
  system-serial\x2dgetty.slice                                                 loaded active active    Slice /system/serial-getty
  system-systemd\x2dfsck.slice                                                 loaded active active    Slice /system/systemd-fsck
  system-xfs_scrub.slice                                                       loaded active active    xfs_scrub background service slice
  system.slice                                                                 loaded active active    System Slice
  user-1000.slice                                                              loaded active active    User Slice of UID 1000
  user.slice                                                                   loaded active active    User and Session Slice
  acpid.socket                                                                 loaded active running   ACPID Listen Socket
  cloud-init-hotplugd.socket                                                   loaded active listening cloud-init hotplug hook socket
  dbus.socket                                                                  loaded active running   D-Bus System Message Bus Socket
  dm-event.socket                                                              loaded active listening Device-mapper event daemon FIFOs
  iscsid.socket                                                                loaded active listening Open-iSCSI iscsid Socket
  lvm2-lvmpolld.socket                                                         loaded active listening LVM2 poll daemon socket
  lxd-installer.socket                                                         loaded active listening Helper to install lxd snap on demand
  polkit-agent-helper.socket                                                   loaded active listening Authorization Manager Agent Helper
  snapd.socket                                                                 loaded active running   Socket activation for snappy daemon
  ssh.socket                                                                   loaded active running   OpenBSD Secure Shell server socket
  sshd-unix-local.socket                                                       loaded active listening OpenSSH Server Socket (systemd-ssh-generator, AF_UNIX Local)
  syslog.socket                                                                loaded active running   Syslog Socket
  systemd-ask-password.socket                                                  loaded active listening Query the User Interactively for a Password
  systemd-creds.socket                                                         loaded active listening Credential Encryption/Decryption
  systemd-factory-reset.socket                                                 loaded active listening Factory Reset Management
  systemd-hostnamed.socket                                                     loaded active listening Hostname Service Socket
  systemd-journald-dev-log.socket                                              loaded active running   Journal Socket (/dev/log)
  systemd-journald.socket                                                      loaded active running   Journal Sockets
  systemd-logind-varlink.socket                                                loaded active running   User Login Management Varlink Socket
  systemd-mute-console.socket                                                  loaded active listening Console Output Muting Service Socket
  systemd-networkd-resolve-hook.socket                                         loaded active running   Network Management Resolve Hook Socket
  systemd-networkd-varlink.socket                                              loaded active running   Network Management Varlink Socket
  systemd-networkd.socket                                                      loaded active running   Network Management Netlink Socket
  systemd-resolved-monitor.socket                                              loaded active running   Resolve Monitor Varlink Socket
  systemd-resolved-varlink.socket                                              loaded active running   Resolve Service Varlink Socket
  systemd-rfkill.socket                                                        loaded active listening Load/Save RF Kill Switch Status /dev/rfkill Watch
  systemd-sysext.socket                                                        loaded active listening System Extension Image Management
  systemd-udevd-control.socket                                                 loaded active running   udev Control Socket
  systemd-udevd-kernel.socket                                                  loaded active running   udev Kernel Socket
  systemd-udevd-varlink.socket                                                 loaded active running   udev Varlink Socket
  uuidd.socket                                                                 loaded active listening UUID daemon activation socket
  basic.target                                                                 loaded active active    Basic System
  boot-complete.target                                                         loaded active active    Boot Completion Check
  cloud-config.target                                                          loaded active active    Cloud-config availability
  cloud-init.target                                                            loaded active active    Cloud-init target
  cryptsetup.target                                                            loaded active active    Local Encrypted Volumes
  getty-pre.target                                                             loaded active active    Preparation for Logins
  getty.target                                                                 loaded active active    Login Prompts
  graphical.target                                                             loaded active active    Graphical Interface
  imports.target                                                               loaded active active    Image Downloads
  integritysetup.target                                                        loaded active active    Local Integrity Protected Volumes
  local-fs-pre.target                                                          loaded active active    Preparation for Local File Systems
  local-fs.target                                                              loaded active active    Local File Systems
  multi-user.target                                                            loaded active active    Multi-User System
  network-online.target                                                        loaded active active    Network is Online
  network-pre.target                                                           loaded active active    Preparation for Network
  network.target                                                               loaded active active    Network
  nss-lookup.target                                                            loaded active active    Host and Network Name Lookups
  paths.target                                                                 loaded active active    Path Units
  remote-fs-pre.target                                                         loaded active active    Preparation for Remote File Systems
  remote-fs.target                                                             loaded active active    Remote File Systems
  slices.target                                                                loaded active active    Slice Units
  snapd.mounts-pre.target                                                      loaded active active    Mounting snaps
  snapd.mounts.target                                                          loaded active active    Mounted snaps
  sockets.target                                                               loaded active active    Socket Units
  swap.target                                                                  loaded active active    Swaps
  sysinit.target                                                               loaded active active    System Initialization
  time-set.target                                                              loaded active active    System Time Set
  timers.target                                                                loaded active active    Timer Units
  veritysetup.target                                                           loaded active active    Local Verity Protected Volumes
  apt-daily-upgrade.timer                                                      loaded active waiting   Daily apt upgrade and clean activities
  apt-daily.timer                                                              loaded active waiting   Daily apt download activities
  dpkg-db-backup.timer                                                         loaded active waiting   Daily dpkg database backup timer
  e2scrub_all.timer                                                            loaded active waiting   Periodic ext4 Online Metadata Check for All Filesystems
  fstrim.timer                                                                 loaded active waiting   Discard unused filesystem blocks once a week
  fwupd-refresh.timer                                                          loaded active waiting   Refresh fwupd metadata regularly
  logrotate.timer                                                              loaded active waiting   Daily rotation of log files
  man-db.timer                                                                 loaded active waiting   Daily man-db regeneration
  motd-news.timer                                                              loaded active waiting   Message of the Day
  sysstat-collect.timer                                                        loaded active waiting   Run system activity accounting tool every 10 minutes
  sysstat-rotate.timer                                                         loaded active waiting   Rotate daily system activity data file at midnight
  sysstat-summary.timer                                                        loaded active waiting   Generate summary of yesterday's process accounting
  systemd-tmpfiles-clean.timer                                                 loaded active waiting   Daily Cleanup of Temporary Directories
  update-notifier-download.timer                                               loaded active waiting   Download data for packages that failed at package install time
  update-notifier-motd.timer                                                   loaded active waiting   Check to see whether there is a new version of Ubuntu available
  xfs_scrub_all.timer                                                          loaded active waiting   Periodic XFS Online Metadata Check for All Filesystems

Legend: LOAD   → Reflects whether the unit definition was properly loaded.
        ACTIVE → The high-level unit activation state, i.e. generalization of SUB.
        SUB    → The low-level unit activation state, values depend on unit type.

193 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.

LOG COMMANDS:
journalctl -u service
<img width="1347" height="162" alt="image" src="https://github.com/user-attachments/assets/2a1fb52b-9581-4ce5-9b50-9292188330f4" />

