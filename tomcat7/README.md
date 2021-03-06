# Ansible Role: Tomcat 7

安装tomcat7应用

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible `2.2.1.0`
os `Centos 6.7 X64`

## 角色变量
	
	software_files_path: "/opt/software"
	software_install_path: "/usr/local"

	java_home: "{{ ansible_env.JAVA_HOME | default(false) }}"

	tomcat7_version: "7.0.75"
	tomcat7_file: "apache-tomcat-{{ tomcat7_version }}.tar.gz"
	tomcat7_path: "{{ software_install_path }}/apache-tomcat-{{ tomcat7_version }}"
	tomcat7_file_path: "{{ software_files_path }}/{{ tomcat7_file }}"
	tomcat7_file_url: "http://apache.fayea.com/tomcat/tomcat-7/v{{ tomcat7_version }}/bin/apache-tomcat-{{ tomcat7_version }}.tar.gz"

	tomcat7_enabled: true
	tomcat7_server_active: false
	tomcat7_ajp_active: false
	tomcat7_hostname: localhost
	tomcat7_user: tomcat
	tomcat7_server_port: 8005
	tomcat7_catalina_port: 8080
	tomcat7_catalina_ajp_port: 8009
	tomcat7_catalina_redirect_port: 8443
	tomcat7_services_name: "tomcat{{ tomcat7_catalina_port }}"

	tomcat7_work_path: "{{ software_install_path }}/{{ tomcat7_services_name }}"
	tomcat7_CATALINA_OPTS: "-server -Xms512m -Xmx2000m -XX:PermSize=256m -XX:MaxPermSize=2048 -Dfile.encoding=UTF-8 -Dsun.jnu.encoding=UTF-8"

	
## 依赖

java

## github地址

https://github.com/kuailemy123/Ansible-roles/tree/master/tomcat7

## Example Playbook

	- hosts: servers
	  roles:
	   - tomcat7   

	- hosts: servers
	  roles:
	   - { role: tomcat7, tomcat7_catalina_port: 8081}
	   - { role: tomcat7, tomcat7_catalina_port: 8082}


