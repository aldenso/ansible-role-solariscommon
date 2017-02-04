solariscommon
=============

Common configuration for Solaris services (timezone, dns, nsswitch, etc).

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below.

    solariscommon_be: false
    solariscommon_bename: "solaris"
    solariscommon_timezone: "America/Caracas"
    solariscommon_dns_servers: "192.168.56.1 192.168.56.101"
    solariscommon_dns_search: '"aldoca.local" "aldoca.local.ve"'
    solariscommon_ns_switch: '"files dns"'
    solariscommon_ntp_servers: [ '0.pool.ntp.org prefer', '1.pool.ntp.org', '2.pool.ntp.org' ]
    solariscommon_banner: |
      ##################################################################
      Authorized users only. All activity may be monitored and reported.
      ##################################################################

**Important**: check vars/main.yml before you set a variable, some astrings in svccfg may cause trouble without the necessary quotes.

To check timezones availables in Solaris --> /usr/share/lib/zoneinfo/

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: aldenso.solariscommon, solariscommon_be: true, timezone: "America/New_York",  ns_switch: '"files dns mdns"', when: "ansible_os_family == 'Solaris'", become: true }

License
-------

BSD

Author Information
------------------

aldenso@gmail.com