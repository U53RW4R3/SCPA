# Installation

Search Tag(s): #sliver #command-and-control

## Dependencies

Install the required dependencies according to your package manager.

```
$ sudo apt install -yqq gpg curl build-essential mingw-w64 binutils-mingw-w64 g++-mingw-w64

$ sudo dnf -y install gnupg curl gcc gcc-c++ make mingw64-gcc

$ sudo pacman -S go mingw-w64-binutils mingw-w64-gcc curl
```

## Install Sliver

> [!NOTE] Updating Sliver C2
> You can use this script to update sliver C2 if the `update` builtin command doesn't work sometimes due to huge size of binaries.

```
$ wget -qO- https://sliver.sh/install | sudo bash

$ curl https://sliver.sh/install | sudo bash
```

## Compile

### 01 - Compile Sliver for Linux system

```
$ git clone https://github.com/BishopFox/sliver.git && \
cd sliver && ./go-assets.sh && \
make linux && make linux-arm64
```

### 02 - Compile Sliver for Windows system

```
$ git clone https://github.com/BishopFox/sliver.git && \
cd sliver && ./go-assets.sh && \
make windows && make windows-arm64
```

### 03 - Compile Sliver for Mac OSX system

```
$ git clone https://github.com/BishopFox/sliver.git && \
cd sliver && ./go-assets.sh && \
make macos && make macos-arm64
```

## Troubleshoot and Update

```
$ sudo systemctl stop sliver && \
sudo rm -rf /root/.sliver/ /root/.sliver-client/ /home/$USER/.sliver/ /home/$USER/.sliver-client/ && \
sudo cp /home/$USER/Downloads/sliver-server_linux /home/$USER/Downloads/sliver-client_linux /root/ && \
sudo cp /root/sliver-server_linux /root/sliver-server && \
sudo cp /home/$USER/Downloads/sliver-client_linux /usr/local/bin/sliver-client && \
sudo chmod 755 /root/sliver-client_linux /root/sliver-server /usr/local/bin/sliver-client && \
sudo systemctl daemon-reload && \
sudo systemctl start sliver
```