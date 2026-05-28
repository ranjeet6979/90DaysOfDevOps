Explain process states (running, sleeping, zombie, etc.)

List 5 commands you would use daily
ls
cat
mv
cp
less
head
tail
vi

Linux boot process
1. First we press Power ON button i.e. we provide electricity to the motherboard
2. Motherboard has BIOS which is firmware (Basic input output system), BIOS/UEFI loads the bootloader from disk (MBR/EFI partition)
3. Bootloader knows where linux kernel is stored and its loads a Kernel
4. Kernel starts a systemd process which is first process with PID: 1
5. systemd starts other processes like docker, K8s.
