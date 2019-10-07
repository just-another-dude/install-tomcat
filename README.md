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
