# How to get back on track in AWS EC2 if you errnoneously changed the whole /home/ec2-user/ folder permissions #

If you change the permission of the ec2-user you won't be able to login again, 
and the reason for this is that since in AWS EC2 it is allowed only login through the private key,
the permission of the home user folder should be correctly defined.

## Requirements ##

* another EC2 in the same availability zone that you are able to connect to ;)

## Steps ##

### 1. Shut down the old vm ###

First shut down the old VM that we'll cal _VM-corr_ (corrupted)

### 2. Detach the volume ###

Detaching the volume will allow you to mount it on another machine

### 3. Attach the volume onto another machine in the same avail zone ##
Now attach it to a new machine. It should give you a /dev/sdX something. 
Be sure that it's not used (amazon probably already knows this, but check it to be sure)

Let's suppose it's created on /dev/sdf

### 4. Mount it ###

```bash
sudo mkdir -p /vol-corruptedPermissions
sudo mount /dev/sdf /vol-corruptedPermissions
```
### 5. Fix the permissions on the ec2-user home ###
```bash
sudo chmod 700 /vol-corruptedPermissions/home/ec2-user/.ssh
sudo chmod 600 /vol-corruptedPermissions/home/ec2-user/.ssh/authorized_keys
sudo chmod 644 /vol-corruptedPermissions/home/ec2-user/.ssh/known_hosts
sudo chmod 700 /vol-corruptedPermissions/home/ec2-user
```
### 6. Unmount it ###

```bash
sudo umount /vol-corruptedPermissions
sudo rmdir /vol-corruptedPermissions
```

### 7. Detach it and reattach it ###
Detach the volume and attach it again on the original VM. Be sure to attach it on /dev/sda1 (the default. or if you had something different, the right endpoint)

### 8. Power up the machine ###