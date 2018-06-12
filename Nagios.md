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
       
  3. **Object Definitions**
  
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
   6) **Host Can have parent/chod dependency relationship**
   7) **object Inheritance**
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
   
  **plugins**
   
   
   
   **Templates**
     Coming soon
