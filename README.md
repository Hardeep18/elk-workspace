### Run Elasticsearch & Kibana as docker containers
```
git clone https://github.com/Hardeep18/elk-workspace.git
cd elk-workspace/docker-7.1.1 
sudo sysctl -w vm.max_map_count=262144
docker-compose up -d
```
### Install Filebeat on client machine (Ubuntu 18.04)
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
sudo apt-get update && sudo apt-get install filebeat
```
### Configure Filebeat and enable system module
Edit filebeat configuration and update kibana and elasticsearch url
```
sudo vi /etc/filebeat/filebeat.yml
```
```
sudo filebeat modules enable system
sudo filebeat test config
sudo filebeat test output
sudo filebeat setup
sudo systemctl start filebeat
```
