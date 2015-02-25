# ansible-plasticscm

An Ansible role for installing [Plastic SCM](https://www.plasticscm.com/) on Ubuntu 14.04 or Debian 6.0.

Also configures the ufw firewall with only ports 22 and the port set in `plasticscm_port` open.

For more info on installing Plastic SCM, see:

* https://www.plasticscm.com/plastic-for-linux/index.html

## Usage

In your role's meta, add a dependency to this role using the syntax described below.

```yaml
# my_role/meta/main.yml
dependencies:
  - role: jbroadway.plasticscm
    plasticscm_distro: "Ubuntu_14.04"
    plasticscm_port: 8087
```

See the [examples](./examples/) directory for an example playbook.

## Variables

The following variables can be modified:

* `plasticscm_distro` defaults to `Ubuntu_14.04` (for Debian, set to `Debian_6.0`)
* `plasticscm_port` defaults to `8087`
* `plasticscm_data_dir` defaults to `/var/lib/plasticscm/data`
* `plasticscm_conf_dir` defaults to `/var/lib/plasticscm/conf`

## Next Steps

Log into your server and configure the Plastic SCM server:

```bash
cd /opt/plasticscm5/server
sudo clconfigureserver
```

* For "Configuring users/security working mode" choose "UPWorkingMode" so that Plastic SCM will manage usernames and passwords.
* Set the port to the number in your `plasticscm_port` setting.

To create user accounts, run:

```bash
sudo umtool createuser <username> <password> 
```

> Note: Users can change their password later from the client.

Finally, to install your Plastic SCM license, overwrite `/opt/plasticscm5/server/plasticd.lic` with your license file.

Happy hacking!

-----

Brought to you by [The Campfire Union](https://www.campfireunion.com/).
