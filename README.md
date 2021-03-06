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
- **Nginx**
- **PHP 7.2** based on ppa:ondrej/php repo (https://launchpad.net/~ondrej/+archive/ubuntu/php). To add additional PHP extensions, please update https://github.com/nemke82/magento2gitpod/blob/master/.gitpod.Dockerfile#L15 block.
- **Python** (base version)
- **rsync**
- **mc** (Midnight commander)
- **MySQL** (Oracle) 5.7 version
- **xDebug** (latest version). Note: Uncomment lines in https://github.com/nemke82/magento2gitpod/blob/master/.gitpod.Dockerfile#L36 if you need additional options enabled.
- **Blackfire**. Note: Please run **./blackfire-run.sh** to enter your Server/Client ID and Token's. Sometimes it requires extra PHP-FPM restart, so please run service php7.2-fpm restart if required.
- **Tideways**. Note: Please run **/usr/bin/tideways-daemon --address 0.0.0.0:9135 &** to initiate daemon. Please update .env-file located in repo with TIDEWAYS_APIKEY
- **Redis**. Note: Please run 'redis-server &' to start it or run it without & in the separate tab.
- **ElasticSearch 5.6.16**. Note: Please run following command to start it: <BR>
  '$ES_HOME/bin/elasticsearch -d -p $ES_HOME/pid -Ediscovery.type=single-node' <BR>
  
  Some extensions like ElasticSuite (https://github.com/Smile-SA/elasticsuite/wiki/ServerConfig-5.x) requires two ElasticSearch plugins to be installed. You can install them with the following commands:<BR>
  
  $ES_HOME/bin/elasticsearch-plugin install analysis-phonetic <BR>
  $ES_HOME/bin/elasticsearch-plugin install analysis-icu <BR>

Every listed service installation code is added within .gitpod.Dockerfile
You can split them into separate workspaces and share it among themself if you know what you are doing.

TO INSTALL Magento 2.3.3 (latest):
start **./m2-install.sh** once workspace deployed

MySQL:
username: root <BR>
no password defined

Create database, example: <BR>
mysql -e 'create database nemanja;' <BR>

In case you need to adjust certain my.cnf settings, please edit https://github.com/nemke82/magento2gitpod/blob/master/mysql.cnf file and redeploy GitPod workspace.

**Discovered bugs:**
Sometimes it may happen that the exposed port 8002 used for Nginx does not work when tab is loaded in browser. To fix that, either stop/start workspace or destroy it and start process again. <BR>

If you are moving your own installation don't foget to adjust following cookie paths: <BR>
**web/cookie/path to "/"**
**web/cookie/domain to ".gitpod.io"**
  
You may fork this repo and boot it on your own server or local computer:
https://www.gitpod.io/docs/self-hosted/latest/self-hosted/
