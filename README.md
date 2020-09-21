# SshConfig

This role will create/update the /home/<username>/.ssh/config file.  There are two different configs, one for Work, one for Home.

#### Variables

| Parameter | Choices | Comments |
| --------- | ------- | -------- |
| `UserName`| | Username where config will be copied to|
| `SshCustomConfig`| | This is where the .ssh/config file entries should be placed|


#### Example role execution

```
      - role: SshConfig
        vars:
          Location: "home"
          UserName: "jpetro"
          SshCustomConfig:
            - Host: "hostname"
              Hostname: "192.168.129.1"

      - role: SshConfig
        vars:
          Location: "home"
          UserName: "jpetro"
          SshCustomConfig:
            - Host: "gitea gitea.johnpetro.com"
              Hostname: "home.johnpetro.com"
              Options: |
                  Port 3000
                  User git
            - Host: "gitea2 gitea2.johnpetro.com"
              Hostname: "home2.johnpetro.com"
              Options: |
                  Port 3002
                  User git


```

#### Misc Notes 

In the template, the `%- endif -%`  means that the trailing whitespace will be stripped out.