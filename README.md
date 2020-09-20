# SshConfig

This role will create/update the /home/<username>/.ssh/config file.  There are two different configs, one for Work, one for Home.

#### Variables

| Parameter | Choices | Comments |
| --------- | ------- | -------- |
| `UserName`| | Username where config will be copied to|
| `Location` | Choices:<ul><li>home</li><li>work</li></ul> |Set for customizations I have for work or home.|
| `SshCustomConfig`| | This is where any non-default configs for the .ssh/config file would go for a user|


#### Example role execution

```
roles:
  - role: SshConfig
    vars:
      UserName: "testuser"
      Location: "home"

roles:
  - {role: SshConfig, UserName: "testuser", Location: "home"}
  
```

Adding a custom rule:

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

```