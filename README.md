# restore-ssh-keys-from-backup
This repository demonstrates how to restore SSH key pairs from backup and fix its UNIX files permissions

## Check default permissions for newly generated ssh key pair

```bash
mkdir -p $HOME/.ssh
ssh-keygen -t rsa -b 4192 -N "" -C "Test ssh key pair created at: `date`" -f $HOME/.ssh/test_id
ls -lah ~/.ssh
```

## Fix permissions of copyed ssh files

```bash
mkdir -p /tmp/.ssh
cp -Rf /path/to/backup-dir /tmp/.ssh
sudo chmod -Rfv a-rwx /tmp/.ssh/*
sudo chmod -Rfv u+rw /tmp/.ssh/*
sudo chmod -Rfv go+r /tmp/.ssh/*.pub
sudo chmod -Rfv 644 /tmp/.ssh/config || echo 'Oops, seems like config file has not beed found.'
ls -lah /tmp/.ssh
```
