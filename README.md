# General
Project dedicated to installing Tomcat with Ansible (tested on Tomcat 9).  
This was tested running the playbook locally on a CentOS 7 machine with Ansible 2.4 and Python 2.7.5.
  
  
# Requirements
* The user must be able to become root (sudo priviliges).  
* CentOS 7 machine (although other distros might work).  
* Ansible 2.4 (although other versions might work).  
* Python 2.7.5 (although other versions might work).  
* You must have a valid URL for the playbook to download Tomcat from.
Link: https://tomcat.apache.org/download-90.cgi  
Choose the "Core" binary distribution and use the link from the "tar.gz" option.  
As of 7.10.19, the current URL for me is: https://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.26/bin/apache-tomcat-9.0.26.tar.gz  
  
  
# Variables
| Name | Required | Type | Example |
| ---- | -------- | ---- | ------- |
| tomcat_download_url | Yes | String | https://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.26/bin/apache-tomcat-9.0.26.tar.gz |
  
   
# Usage Example
ansible-playbook -vvvvv -e "tomcat_download_url=https://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.26/bin/apache-tomcat-9.0.26.tar.gz" site.yml
  
  
# Notes
1) The playbook is used with commandline arguments and not with a prompt.  
2) The download link is dynamic, therefore it must be rechecked before running the playbook each time.  
3) This playbook does not include adding users for managing tomcat, therefore it must be done later.
4) The playbook makes the tomcat server listen on port 8090 and not the default 8080. This can be changed in the config file: /opt/tomcat/latest/conf/server.xml ; Replace all strings containing 8090 with 8080.
5) As part of my Ansible learning process, I realized that commandline arguments (--extra-vars) are sent as named arguments. If there is a variable in a role, it will be sent to the role when calling it using the 'include_role' module. Therefore, in the case of commandline arguments, there is no need of specifying a variable in the playbook itself with the 'vars' module. The 'vars' module inside the playbook is to be used only when passing the variable from the playbook itself to the relevant role and not from outside.  
