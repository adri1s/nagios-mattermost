Nagios Mattermost Plugin
========================

[![langage](https://img.shields.io/badge/Langage-Python-green.svg)](https://www.python.org/)

A plugin for [Nagios](https://www.nagios.org/) and compatible software (e.g. [Icinga](https://www.icinga.org/)) to enable notifications to a [Mattermost](http://www.mattermost.org/) server.

## Plugin Usage

Run `./mattermost.py --help` for full usage information.

## Mattermost Configuration

1. *Incoming Webhooks* must be enabled for your Mattermost server. Check the **Enable Incoming Webhooks** option under **Service Settings** in the *System Console*.

2. To use the optional `--username` parameter you must enable overriding of usernames from webhooks. Check the **Enable Overriding Usernames from Webhooks and Slash Commands** option under **Service Settings** in the *System Console*.

3. To use the optional `--iconurl` parameter you must enable overriding of icons from webhooks. Check the **Enable Overriding Icon from Webhooks and Slash Commands** option under **Service Settings** in the *System Console*.

## Nagios Configuration

The steps below are for a Nagios 4 server but should work with minimal modifications for compatible software:

1. Copy `mattermost.py` to `/usr/local/nagios/libexec`.

2. Create an *Incoming Webhook* integration for the approriate team and note the provided URL.

3. copy configuration `mattermost.cfg` to `/etc/nagios4/conf.d/`  and upgrade parameter <MATTERMOSTE_URL>, <MATTERMOSTE_CHANNEL> and <NAGIOS_CGIURL>

4. Add the contact to a contact group in your Nagios configuration:
```
define contactgroup{
    contactgroup_name       network-admins
    alias                   Network Administrators
    members                 email, mattermost
}
```