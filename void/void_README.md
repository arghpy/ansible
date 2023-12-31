# Ansible Void Gnome

Install voidlinux with gnome desktop environment (DE) through ansible.

## Requirements

- Ansible
- python3

## Setup

This is the setup needed before running the playbook.

1. Download voidlinux iso:

Go to https://repo-default.voidlinux.org/live/current/ and download the base iso image.

2. Copy the iso image on a USB stick by either using `dd` or other tools:

```
#: dd if=/path/to/iso of=/dev/XXX bs=4096 status=progress
```

3. Clone the repository:

```
$: git clone https://github.com/arghpy/ansible_void_gnome.git

```

4. Boot the client from the USB stick.

5. Log in as `anon`.

6. Put the IP of the client in place of <IP> placeholder in `hosts`:

You can view the IP of the client by running:

```
$: ip addr show
```

```
[local]
<IP>

[local:vars]
ansible_user = root
ansible_ssh_private_key_file = ~/.ssh/id_ed25519
```

7. Create an ssh key for your user:

```
$: ssh-keygen
```

8. Copy the key on the target client:

```
$: ssh-copy-id root@<IP>
```

9. Run the command from `void_cmds.txt` on the client machine:

```
$: sudo xbps-install -Syu xbps python3.11 && sudo ln -s /usr/bin/python3.11 /usr/bin/python3 && sudo ln -s /usr/bin/python3.11 /usr/bin/python && sudo mkdir /root/.ssh && sudo cp .ssh/authorized_keys /root/.ssh
```

NOTE: at the moment of this writing python3.11 was needed in order to perform some tasks

10. Run the playbook from the master:

```
$: ansible-playbook playbooks/installation.yml
```
