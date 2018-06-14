# Nagios 
  A Monitoring tool for hosts and applications.

## Nagios Features

  1. **Infrastructure Monitoring**
  
       * Provided by Nagios Core
       * Uses Standard protocols: ICMP,TCP,UDP,etc
       * Host Resources: Disk | CPU | Ram usage - NRPE - Addon
       * Event Handler for service Restarts across platforms: Linux | Unix | windows | etc
       * checks are performed every 5-minutes by default, unless overridden via HOST,HOSTGROUP,SERVICE,etc..
       * Active Checks and Passive Checks
       
  2. **Modular**
  
       * Nagios Core - Main Monitoring Engine
       * Nagios XI - Commericial Monitoring Engine
       * plugins
       
  3. [**Object Definitions**](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/objectdefinitions.html)
  
       * Hosts
       * Services - HTTP,SMTP,DNS,etc
       * Contacts - People who should me notified
       * Contact group
       * Host groups
       * Service groups
       * commands
       * Time Period - i.e when to check host-availability and when to notify
       etc..
       
   4) **Optional Per-Object Monitoring schedule**
   5) **Scheduled Templates**
   6) **Host Can have parent/child dependency relationship**
   7) [**object Inheritance**](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/objectinheritance.html)
   8) **Service Dependencies**
   9) **Varios Notification**
       * SMS
       * E-mail
       * Slack Api
       
  10) **Notification Schedules**
  11) **Notification States**
         * Critical 
         * Warning
         * Unknown
         * Ok
  12) **Extensible via community Addons**
         - NRPE
         - NSClient++
  
## Installation

  **Features**
  
   1) Configures required items, including Apache Httpd
   2) Auto-monitoring of localhost(127.0.0.1)

   Note: Postfix or SMTP needs to be installed for e-mail configuration
   
  **Installations**
  
   1) `aptitude search nagios`
   2) `aptitude install nagios3`
   3) `dpkg -l | grep -i nagios3`
   
## Configurations

   **Nagios.cfg**
   
   It is the main file in the location `/etc/nagios3/nagios.cfg`. When nagios starts up it checks the `nagios.cfg ` file to check the configuration.
   
   * 'cfg_file' - specifies config file to include: i.e hosts,services,contacts,etc..
   * 'cfg_dir'  - specifies directory to include,containing config files (\*.cfg) to process
   
  **Plugins**
   
   * `/etc/default/nagios3` - influences daemon-startup
   * `/usr/share/nagios3/plugins` - Event handlers
   * `/etc/nagios-plugins` - Contains pre-rolled checks
   * `/usr/lib/nagios/plugins` - repository of varios checks: i.e 'check_tcp','check_icmp',etc.
  
  ***ICMP (PING) Monitoring***
    
   1) Ping Monitoring using: '/usr/lib/nagios/plugins/check_host -> check_ping'
   2) Pre-defined templates to handle most monitors:
       * 'generic-host' - checks target using ICMP with sensible defaults
       * 'generic-host; - can be inherited by HOST Definition using: `use generic-host`
   3) Hosts and various objects are read from   `/etc/nagios3/conf.d`.
   
  **Reloading Configurations**
  
    -  `/etc/init.d/nagios3 reload`
    
  ***TCP/UDP Monitoring*** 
  
## Three Kinds of Remote Execution

  ***Check By SSH***
    
   - By default,`check_by_ssh` plugin is already in the plugin directory.
   - This is a direct execution on the client machines.
    
  ***NRPE***
  
   -  Install NRPE agent on the hosts
        `aptitude install nagios-nrpe-server`
   -  Configuration file for nrpe is `/etc/nagios/nrpe.cfg`  and in the configutaion file add the nagios master server ip address in the allowed hosts.
   -  Change the server address to "0.0.0.0"
   _  A NRPE Daemon will be running on all the client machines.(Linux)
   
   ***NCPA***
   
   - Cross Platform a Client side agent, no plugin required.
   - NCPA Automatically measures
       * CPU
       * Memory (Swap & RAM)
       * Network Utilization
       * Disk Utilization
   
## Nagios At Scale, Distribute all the things

  **Nagios Scaling**

   - Nagios forks for each service check.
   - `ps -fC nagios` will list multiple forks for service checks.
   - Nagios puts all the forked requested responses to the `/usr/local/nagios/var/spool`.
   
   *Repear Operation*
   
   - Internal Nagios Operation
   - Grabs check results from the spool directory.
   - Serializing the processing of check results.
  
  To scale nagios effectively,
    * Cheaper forking
    * Faster Reaping
  
  *Passive Checks*
  
  - Eliminates forking altogether
  - Making reaping faster and less expensive
  
  *Large Scale with Mod_Gearmen*
  
  - Uses Queuing Mechanism

## 
  
