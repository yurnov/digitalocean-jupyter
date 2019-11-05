Running Jupyter on Digital Ocean to learn Python 3
=========

Short Ansible playbook and roles to create droplet with running Jupyter notebook in DigitalOcean to learn Python 3 and destroy droplet after lerning to save costs.

It created mostly to be used as lab enviroment for Python training.

Requirements
------------

Pre-requisites is DigitalOcean account (you may use my referal link https://m.do.co/c/ac7511463eef for registartion and you will get gets $50 in credit over 30 days) and API access token. If you haven't access token navigate to https://cloud.digitalocean.com/account/api/tokens and click to Generate New Token button, do not forget to allow write permitions. As well, you need to have ssh-key added you your DigitalOcean profile (you do not add key yet, go to https://cloud.digitalocean.com/account/security and do so). This kay will be used to access and provision your droplet. Latest added key will be used you you have added several.  

Variables
--------------

Recommended droplet size is `s-2vcpu-4gb` that cost just $0.03/hour, anyway, default one is smallest one `s-1vcpu-1gb` that cost $0.007/hour. Default DigitalOcean region is `ams3`. This is defined in playbook/do_create_droplet/defaults/main.yml  

Anyway, you may override this defaults by extravar, for example:

 `ansible-playbook create_jupyther.yml -e "droplet_size=s-2vcpu-4gb droplet_region=sfo2"`

Dependencies
------------

Ansible (tested on version 2.8.3) and ansible dependencies, like python. Python modules `jmespath` requried to work with json. I you haven't, please install by following:

```
pip install ansible==2.8.5
pip install jmespath
```

Native docker module do not used to avoid dependency of docker or docker-py
  

Example Run
----------------

You should provide DigitalOcean API token with write permission to be able to use this playbook/roles, example to run for create Jupyter:

 `ansible-playbook create_jupyther.yml -e "do_api=c010187272c8a7b5bff5bfr5bdrced563bfrlbc4846539bdrv0985ca2b847cbda"`

to destroy droplet:

`ansible-playbook delete_jupyther.yml -e "do_api=c010187272c8a7b5bff5bfr5bdrced563bfrlbc4846539bdrv0985ca2b847cbda"`

This is not valid key, you should use your own key instead! 


