SshConfig
=========

This role will create/update the /home/<username>/.ssh/config file.  There are two different configs, one for Work, one for Home.

Requirements
------------
None

Role Variables
--------------

| Parameter | Comments |
| --------- | -------- |
| `UserName`| Username where config will be copied to|
| `SshCustomConfig`| This is where the .ssh/config file entries should be placed|


Example Playbook
----------------

Single User Config
```
      - role: SshConfig
        vars:
          SshCustomConfig:
            - UserName: testuser
              Entry: |  
                Host: *
                  ForwardAgent yes

```

Multiple User Configs

```
      - role: SshConfig
        vars:
          SshCustomConfig:
            - UserName: testuser
              Entry: |  
                Host: *
                  ForwardAgent yes
                Host github.com
                  Hostname github.com
                  PreferredAuthentications publickey
                  IdentityFile ~/.ssh/github_testuser
            - UserName: root
              Entry: |  
                Host github.com
                  Hostname github.com
                  IdentityFile ~/.ssh/github_testuser
                Host gitea.example.com
                  Hostname gitea.example.com
                  IdentityFile ~/.ssh/gitea_testuser


```

License
-------
MIT

Author Information
------------------

* This role was created in 2020 by [John Petro](https://github.com/jcpetro97)
* Code updated to V2 in 8/2022
