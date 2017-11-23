# QEMU-WRAPPER
KVM QEMU Wrapper for enabling TX and RX Queue size on VirtIO devices

## Install
CentOS and RHEL distributions

Make sure of not overwritting the original qemu-kvm binary file

```shell
# Move the original qemu-kvm binary to a different location
mv /usr/libexec/qemu-kvm /usr/libexec/qemu-system-x86_64

# Copy the wrapper at the qemu-kvm original location
cp ./qemu-kvm /usr/libexec/qemu-kvm

# Make it executable
chmod +x /usr/libexec/qemu-kvm

# Copy original SELinux context to the wrapper
semanage fcontext -a -e /usr/libexec/qemu-system-x86_64 /usr/libexec/qemu-kvm

# Apply SELinux context to both wrapper and origianl qemu-kvm binary
restorecon -vvRF  /usr/libexec/qemu-system-x86_64
restorecon -R -v /usr/libexec/qemu-kvm
```
