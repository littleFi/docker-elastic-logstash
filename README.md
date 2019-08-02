# docker-elastic-logstash
docker版的es和logstash

es 运行
docker network create elasticsearch
docker run -d --name elasticsearch -v /docker/conf/elasticsearch/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml --net elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:5.6.16

logstash运行

docker run --rm -it -v /docker/conf/logstash/:/usr/share/logstash/config/ logstash:5.6.16

进入容器安装jdbc插件和es插件安装jdbc插件
bin/logstash-plugin install logstash-input-jdbc
安装es插件
bin/logstash-plugin install logstash-output-elasticsearch

启动logstash
bin/logstash -f config/address.conf --path.data=/root/

es-head 运行
docker run -d -p 9100:9100 --name elasticsearch-head mobz/elasticsearch-head:5

