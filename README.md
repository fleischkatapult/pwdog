# pwdog
is a secure credential management software utilizing GnuPG for encryption and access control.

## Why?
Existing credential management solutions didn't fit our needs for various reasons - no self-hosting, no built-in workgroup usability, missing audit trail, ...

## Features
### Access control
Credentials can be read and modified only by it's recipients.

### Traceability
pwdog aims to provide a full, trustworthy audit trail of actions on credentials (create, read, change, delete).

### Secure protocol
pwdog is built upon a simple REST API - utilizing GnuPG to authenticate operations on credentials with signatures.

## Getting started
### Setup
To install pwdog on your machine type:

    $ sudo python setup.py install

### Configuration
pwdog has a simple configuration file that should reside in *~/.pwdog/pwdog.conf*:

    [common]
    # optionally set home directory for GPG manually (default: ~/.gnupg)
    #gpg_home_dir = /var/lib/pwdog/gnupg

    [client]
    mykeyid = <your key ID>
    cache_path = /home/<user>/.pwdog
    server = localhost:8080

    [server]
    store = filesystem
    store_path = .

### Starting the server
To start the pwdog server type:

    $ pwdog-server

### Usage

pwdog is simple to use on the command line:

    $ pwdog [-h] {set,get,delete,recipients} ...

The sub commands **set**, **get** and **delete** take a name and type argument.

#### Examples

If you want to save credentials for the root account of foo.example.com, we could type this:

    $ pwdog set foo.example.com login_root

... providing pwdog with a name (i.e. a hostname) and the type of credential (i.e. service) to save.

## Authors
[Patrick Otto](mailto:patrick.otto@mayflower.de) and [Franz Pletz](mailto:franz.pletz@mayflower.de)

