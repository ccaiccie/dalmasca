# Dalmasca: Network DevOps Container

![Dalmasca Tribe](https://raw.githubusercontent.com/packetferret/dalmasca/master/images/dalmasca.png "Dalmasca Tribe")

This container aims to have everything needed to begin automating your network. Since this container will never be a true microservice, but rather an environment to perform your automation / troubleshooting, I have selected Centos as the base image. While this ultimately makes the container much larger, it has everything that I need to do my job (ie. SSH, traceroute, ping, and yum for anything missed).

`image: centos/python-36-centos7:latest`

## Operations

How to use this container

### Pull from Dockerhub

`docker pull packetferret/dalmasca:latest`

This image is a "squashed" image, resulting in half the size but without any layers. For those unfamilar with docker concepts, or don't want to build the container themselves, this is the way to go.

Please note that if you use the image on Dockerhub instead of building it locally with this repo, you lose out on the awesome Makefile commands. Should that be the case, please use the following command to run the container instead:

`docker run -it -v $(pwd):/home/tmp/files -w /home/tmp/files packetferret/dalmasca:latest /usr/bin/zsh`

This will run the container image (packetferret/dalmasca:latest) with the executable of zshell (/usr/bin/zsh), while mounting your current directory ($pwd) in /home/tmp/files; as an added bonus the command will also place you in that path within the container.

Use this command in any directory on your host machine that has automation goodies to run, they'll immediately be presented as your current directory in the container.

Happy automating.

### Building the container

If you're more privy to building the containers, and you're on a *nix workstation with Make installed (build-essentials), then proceed with this method instead.

`make build`

### Run the container

`make run`

Running this container will mount the current directory from your local computer into the container, run `ls -l` inside the container to confirm your files are there

If your files are in another directory, then run the following command in that directory instead.

`docker run -it -v $(pwd):/home/tmp/files -w /home/tmp/files packetferret/dalmasca:latest /usr/bin/zsh`

## Packages installed

This is an incomplete list of packages you may find interesting

- ansible
- aos-pyez (Apstra)
- batfish
- f5-sdk (F5)
- jsnapy (Juniper pre/post checks tool)
- junos-eznc (Juniper PyEZ)
- jxmlease (Juniper XML)
- napalm
- netmiko
- ntc-ansible
- nxapi-plumbing
- pyeapi (Arista EOS)
- pyIOSXR (Cisco IOS-XR)
- textfsm
