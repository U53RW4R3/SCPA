# Setup

## 01 - Install

## 1.1 - Clone the repository from a source forge site

`$ sudo git clone --recurse-submodules https://github.com/cobbr/Covenant /opt/post-exploitation/Covenant`

## 1.2 - Run the C2

### 1.2.1 - Run with dotnet CLI

```
$ export DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1

$ sudo dotnet run --project /opt/Covenant/Covenant
```

### 1.2.2 -  Build and run with docker image

```
$ docker build -t covenant /opt/Covenant/Covenant

$ sudo docker run -it -p 7443:7443 -p 80:80 -p 443:443 --name covenant /opt/Covenant/Covenant/Data:/app/Data covenant
```

## 02 - Troubleshooting

### 2.1 - Restart Covenant

```
$ sudo docker stop covenant

$ sudo docker start covenant -ai
```

### 2.2 - Delete Data

* When running dotnet CLI just remove the SQLite database file and restart from scratch

`$ sudo rm /opt/Covenant/Covenant/Data/covenant.db`

* When running docker to restart from scratch just delete the container and start from scratch

`$ sudo docker rm covenant`

## 03 - Register Initial User

### 3.1 - Register username

* Navigate to this URL with a web browser `https://<C2_IP>:7443`

TODO: Insert screenshot here