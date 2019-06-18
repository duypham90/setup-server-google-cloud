# setup-server-google-cloud

# SSH Key
- https://help.github.com/en/enterprise/2.16/user/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
- copy: pbcopy < ~/.ssh/id_rsa.pub
# Setup server

## Create a New User
```
- sudo adduser dummy
- sudo usermod -aG sudo dummy
- sudo usermod -aG sudo dummy
```

## Switch new user
```
su - dummy
```

## Create .ssh folder

```
- mkdir .ssh
- cd .ssh && touch authorized_keys
- vi authorized_keys
- past ssh key copy from local to authorized_keys
```

# As root or your new sudo user, open the SSH daemon configuration
```
- sudo vi /etc/ssh/sshd_config
- PasswordAuthentication no
- PubkeyAuthentication yes
- ChallengeResponseAuthentication no
- sudo systemctl reload sshd ỏ sudo service sshd restart
```

# Set Up a Basic Firewall
```
- sudo ufw app list
- Output
    Available applications:
    OpenSSH  
- sudo ufw allow OpenSSH
- sudo ufw enable
- sudo ufw status
```
```
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)

```
