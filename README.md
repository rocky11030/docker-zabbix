# zabbix_install

安装说明
========

- 此项目主要是通过ansible+docker安装zabbix的3.0.9版本的zabbix-server和zabbix-agent
- 镜像需要从百度网盘下载
- 问题1: 还有zabbix-server和zabbix-agent的docker镜像启动shell脚本没有弄懂，导致重启docker配置文件就会还原
- 问题2: 有些zabbix-agent不能发现，问题可能是zabbix-server的配置文件的Timeout设置时间过低，以后可以设置Timeout=30
- ansible版本为2.3以上，安装zabbix-server的操作系统可以是ubuntu14.04和centos7.2以上


第一步: 修改变量文件
--------------
* 修改groups_vars/all里面的变量
* 修改hosts主机变量: zabbix_server和zabbix_agent的hosts主机

第二步: 安装zabbix-server和zabbix-agent容器
--------------
* 执行脚本:ansible-playbook -i hosts zabbix_install.yml

第三步: Centos6(内核过低不支持docker)安装zabbix-server
--------------
* 执行脚本:ansible-playbook -i hosts zabbix_agent_centos6.yml
