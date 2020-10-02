# Setting up a Gitea code hosting platform

forked from: https://git.theo-andreou.org/Personal/ansible-deploy-gitea

Gitea is a self-hosted Git-based Code Hosting Platform and a nice alternative to Github and other proprietary services. You can use this Ansible Playbook to host your own Code Hosting Platform under your own control.

This setup offers:

* Gitea
* MariaDB backend
* Nginx reverse proxy
* Fail2Ban Gitea protection
* HTTPS by Let's Encrypt
* SSH on a custom port 4444

## Prerequisites

* A Debian or Ubuntu machine.
* A publicly available FQDN:

```
git.cerveau.us.	300	IN	A	1.2.3.4
```

## Deploy gitea

Clone the repository:

```
$ git clone http://www.github.com/agonzal/ansible-deploy-gitea.git
$ cd ansible-deploy-gitea
```

Prepare a *vars/all.yml* file (you can use *vars/all.yml.example* as reference):

```
# vars/all.yml
gitea_fqdn: git.cerveau.us
gitea_db: gitea
gitea_db_user: gitea
gitea_version: 1.12.4
```

Adjusts the host(s) in *deploy_gitea.yml* as well as other changes (email in cert config, etc..) and run the Playbook:

```
$ ansible-playbook deploy_gitea.yml
```

When done rush to https://git.cerveau.us. First one to create an account gets to be an admin!

Check out [Installing Gitea on Ubuntu][http://agonzal.github.io/2020/installing-gitea/] for some more post-install config changes to gitea for more lockdown control.

References
----------
* https://docs.gitea.io/en-us/install-from-binary/
* https://docs.gitea.io/en-us/linux-service/
* https://dl.gitea.io/gitea/1.12.4/
* https://docs.gitea.io/en-us/fail2ban-setup/
