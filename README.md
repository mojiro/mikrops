# MikrOps
A management UI for MikroTik Routers based onto Django.

MikrOps is a project that tries to bring together all those little services that usually we need to setup our network. DNS, Radius, Syslog, Ansible, monitoring, etc.

Currently Syslog and Ansible are fully integrated and I am trying to solve several small bugs and make the project presentable.

The Ansible integration is based onto the project [YaMa](https://github.com/mojiro/yama) that I wrote last year.

----

## Installation

### Prerequisites
1. Clean Ubuntu Server installation.
2. No running Docker containers. All containers will be removed during installation.

### Prepare installation files

```
cd /opt
git clone https://github.com/mojiro/mikrops
cd mikrops
find . -name '*.sh' | xargs chmod +x
cp config/settings.conf.dist config/settings.conf
```

### Configuration

Edit file `config/settings.conf`

### Installation
```
./install.sh
```

----

## Images

![mikrops area devices](mikrops-area-devices.png)

![mikrops execution start](mikrops-execution-start.png)

![mikrops execution log](mikrops-execution-log.png)
