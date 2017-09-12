# zabbix_install

安装说明
========

- 此项目主要是通过ansible+docker安装zabbix的3.0.9版本的zabbix-server和zabbix-agent
- 镜像需要从百度网盘下载
- 说明1: 如果修改zabbix-server配置文件，需要进入zabbix-server容器注释掉启动脚本/run_zabbix_component.sh里面prepare_server()函数的的 #update_zbx_config "server" "$db_type"
- 说明2: 如果修改zabbix-agent配置文件，需要进入zabbix-agent容器注释掉启动脚本/run_zabbix_component.sh里面prepare_agent()函数的 #prepare_zbx_agent_config
- ansible版本为2.3以上，安装zabbix-server的操作系统可以是ubuntu14.04和centos7.2以上


第一步: 修改变量文件
--------------
* 修改groups_vars/all里面的变量
* 修改hosts主机变量: zabbix_server和zabbix_agent的hosts主机

第二步: 安装zabbix-server(监控zabbix-server的agent注意使用docker网络)和zabbix-agent容器
--------------
* 执行脚本:ansible-playbook -i hosts zabbix_install.yml

第三步: Centos6(内核过低不支持docker)安装zabbix-server
--------------
* 执行脚本:ansible-playbook -i hosts zabbix_agent_centos6.yml
