# MikrOps
A management UI for MikroTik Routers based onto Django.

MikrOps is a project that tries to bring together all those little services
that usually we need to setup our network. DNS, Radius, Syslog, Ansible,
monitoring, etc.

Currently Syslog and Ansible are fully integrated and I am trying to solve
several small bugs and make the project presentable.

The Ansible integration is based onto the project
[YaMa](https://github.com/mojiro/yama) that I wrote last year.

----

## Installation

All external components are being retrieved automatically during the
installation.

### Prerequisites
1. Clean Ubuntu Server installation
2. Static network configuration
3. Full access to internet to download software packages
4. No running Docker containers (existing containers will be removed during
  installation)

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
The following step will last about 10 minutes.
```
./install.sh
```

### Start the containers
```
./daemon.sh start
```

### Create superuser
```
./create_django_superuser.sh
Loading configuration
- Platform: ubuntu

Username: admin
Email: admin@example.com
Password:
```

### Start using MikrOps

During the installation, a Certificate Authority got created using the details
of `settings.conf`. In the following steps you will get prompted to trust and
accept a certificate. It is a safe and required step in order to start using
MikrOps.

#### Mozilla Firefox

1. Open Mozilla Firefox
2. Visit `http://<ip>`
3. Trust and accept a certificate

The certificate has been installed only to Mozilla Firefox

#### Microsoft Windows - Google Chrome (and similar browsers)

1. Open Google Chrome
2. Visit `http://<ip>`
3. The certificate will get downloaded automatically
4. Google Chrome will warn you that this is a dangerous file
5. Click Keep and open the file
6. A window from the Operating System will appear
7. Install Certificate for Current User
8. Guide the installer to install it under 'Trusted Root Certification
  Authorities'

The certificate has been installed to Operating System

### Import initial data

1. Visit `https://<ip>`
2. Login using your credentials
3.

----

## Project components

### Docker containers
- PostGreSQL
- Redis
- RSyslog - Custom build
- Freeradius - Custom build
- Ansible - Custom build
- Django - Custom build
- Celery - Custom build
- Nginx

### Python libraries
- Requests - https://requests.readthedocs.io/
- Psycopg2 - https://pypi.org/project/psycopg2/
- Redis - https://pypi.org/project/redis/
- Celery - https://docs.celeryproject.org/en/latest/django/first-steps-with-django.html

### Django libraries
- django-autocomplete-light - http://django-autocomplete-light.readthedocs.io/
- django-bootstrap4 - https://django-bootstrap4.readthedocs.io/
- django-crispy-forms - https://django-crispy-forms.readthedocs.io/
- django-tables2 - https://django-tables2.readthedocs.io/
- django-treebeard - https://django-treebeard.readthedocs.io/

### CSS / JS libraries
- JQuery - https://github.com/jquery/jquery/
- JQuery UI - https://jqueryui.com/download/all/
- JQuery Form - https://github.com/jquery-form/form/
- Bootstrap - https://github.com/twbs/bootstrap/
- Font Awesome - https://github.com/FortAwesome/Font-Awesome/
- Dripicons - https://github.com/amitjakhu/dripicons/

----

## Images

![mikrops area devices](mikrops-area-devices.png)

![mikrops execution start](mikrops-execution-start.png)

![mikrops execution log](mikrops-execution-log.png)
