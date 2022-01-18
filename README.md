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
mkdir -p ~/.ssh
cp -Rf /path/to/backup-dir ~/.ssh
sudo chmod -Rfv a-rwx ~/.ssh/*
sudo chmod -Rfv u+rw ~/.ssh/*
sudo chmod -Rfv go+r ~/.ssh/*.pub
sudo chmod -Rfv 644 ~/.ssh/config || echo 'Oops, seems like config file has not beed found.'
ls -lah ~/.ssh
```
