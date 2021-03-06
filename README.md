Ansible Role: Clone and Upload Git Repository 1.0
=====================

[![Build Status](https://travis-ci.org/mm0/ansible-role-clone-and-upload-git-repository.svg?branch=master)](https://travis-ci.org/mm0/ansible-role-clone-and-upload-git-repository)


An Ansible role that clones a git repository locally and uploads it to a target host in a compressed and secure manner.  

This allows you to not have to upload a git key or credentials on a remote host to download a repository onto it.

Requirements
---------------

- Local server must have git credentials configured to access repository configured via ssh.  

Role Variables
---------------

Available variables are listed below, along with default values:

```yml
owner: root # owner of final directory uploaded remotely
    group: root
    mode: 644 # mode for remote directory
git_site: github.com # or bitbucket.org, etc
    organization: # git_site organization/user, no default
    repo: # name of the respotiry, no default
    destination: # remote directory for repo to be exported to, no default
    save_old: no # optionally create a backup of the destination directory if it already exists
```

Dependencies
---------------

- tar
- git client

Example Playbook
---------------

```yml
- hosts: webservers
  roles:
    - { role: repo,
            git_site: bitbucket.org
            organization: my_username
            repo: my_repo
            destination: "/var/www",
            save_old: no,
            owner: ubuntu,
            group: ubuntu,
            mode: "0755"
        }
```

License
---------------

BSD-2


Author Information
------------------

[Matt Margolin](mailto:matt.margolin@gmail.com)

[mm0](https://github.com/mm0) on github

