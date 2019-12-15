# magento2gitpod
Magento 2 optimized setup for https://gitpod.io workspace -- Nginx, MySQL, PHP 7.2, PHP-FPM and lot more...

*How-to instructions:*
1) Register on https://gitpod.io 
2) Fork https://github.com/nemke82/magento2gitpod to your repo
3) Install https://chrome.google.com/webstore/detail/gitpod-online-ide/dodmmooeoklaejobgleioelladacbeki?hl=en
4) Load your forked repo and click on green GITPOD button, next to Clone or Download button:
http://i.imgur.com/XZCn57y.png

Gitpod will now launch a workspace container for you in the cloud, containing a full Linux system. It will also clone the GitHub repository branch based on the GitHub page you were coming from.

More info: https://www.gitpod.io/docs/10_getting_started/

Services/Tools installed:
- Nginx
- PHP 7.2 based on ppa:ondrej/php repo (https://launchpad.net/~ondrej/+archive/ubuntu/php)
- Python (base version)
- rsync
- mc (Midnight commander)
- MySQL (Oracle) 5.7 version
- xDebug (latest version). Note: Uncomment lines in https://github.com/nemke82/magento2gitpod/blob/master/.gitpod.Dockerfile#L36 if you need additional options enabled.
- Blackfire installed). Note: Please run ./blackfire-run.sh to enter your Server/Client ID and Token's.
- Redis installed. Note: Please run 'redis-server &' to start it.

TO INSTALL Magento 2.3.3 (latest):
start ./m2-install.sh once workspace deployed

MySQL:
username: root
no password defined

Create database, example:
mysql -e 'create database nemanja;'

In case you need to adjust certain my.cnf settings, please edit https://github.com/nemke82/magento2gitpod/blob/master/mysql.cnf file and redeploy GitPod workspace
