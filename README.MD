# Apache Toolkit Plus Yii2

This toolkit is designed to make virtual host management more easier from command line.

## differences from original Apache Toolkit
`create-host-yii2` command will create virtual host folder structure:
hosts\
     - site.com\
	           - site.com\
			              (put here yii2 files, composer.json, `web` folder, etc)
			   - error.log
			   - requests.log
Document root wil be set to the `hosts\site.com\site.com\web folder`, Pretty URLs are set `On`

## What's inside
This toolkit contains 3 utilites (use it with `sudo`):
* `create-host` - Create a new virtual host (it will prepare all config's and folder)
* `create-host-yii2` - Create a new virtual host (it will prepare all config's and folder, add records to the **/etc/hosts** file) **Only for Ubuntu, yet**
* `delete-host` - Delete a virtual host (including files and config and, **for Ubuntu**, delete previously generated records from the **/etc/hosts** file)
* `edit-host` - Edit host's configuration in VIM.

## Features
* Virtual host management
* Quick configuration edit
* Creating template for new hosts
* Create dns mask for all `.loc` and `.dev` domains (only Ubuntu) **optional**

## Installation
* Clone this repo or go to releases tab and download suitable version.
* Open nessesary distributive folder
* Run `install` file (from your user, not `root` or `sudo`) and follow instructions on screen.

## Builds
* **ubuntu** - Release for all Ubuntu-based products. Updated for Yii2 framework support
* **linux-common** - Rest Linux systems, include only common stuff. (not updated)
* **darwin** - nope

## Support
* Ubuntu      - Supported.
* Debian      - Experimental, may work with ubuntu's package.
* RHEL/CentOS - Supported.
* Darwin/OSX  - nope 

## Usage

### Create virtual hosts
To create virtual host, just run `sudo create-host site.com`.
Tool will create and enable config file and directory for the site.
**(for Ubuntu)** Tool will add `127.0.0.1 site.com` records to the **/etc/hosts** file

### Create virtual hosts for Yii2 Framework (for Ubuntu)
To create virtual host for yii2, just run `sudo create-host-yii2 site.com`.
Tool will create and enable config file and directory for the site and will add `127.0.0.1 site.com` records to the **/etc/hosts** file.
Also Apache will be auto restarted.


### Delete vitrual hosts
To edit host, use `sudo delete-host site.com`.
Also you will be prompted if you want to delete a host directory.
For Ubuntu this command will try to delete previously generated `127.0.0.1 site.com` records from the **/etc/hosts** file

### Edit virtualhost configuration
To edit configuration, use `sudo edit-host site.com`.

### Edit general host configuration template
General template is stored in `/etc/apache-cli/example.conf`.
Yii2 template is stored in `/etc/apache-cli/example-yii2.conf`.
To edit it, you have to use `sudo`.

### Edit Toolkit configuration
Configuration can be found in `/etc/apache-cli/config.sh`.

## Uninstall
To remove toolkit, just run `sudo apache-cli-remove`;
