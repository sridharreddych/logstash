# logstash

http://localhost:8765/api/customer/customers/1
http://localhost:8765/api/customer/customers/2
http://localhost:8765/api/customer/customers/3
http://localhost:8765/api/customer/customers/4


http://192.168.56.101:5601/app/kibana#/discover?_g=(refreshInterval:(pause:!t,value:0),time:(from:'2020-04-08T06:27:52.782Z',mode:absolute,to:'2020-04-08T07:27:52.782Z'))


http://192.168.56.101:9411


now this is the latest working one on april 7th 2020

docker run -p 9200:9200 -p 9300:9300 –-name elasticsearch -d --network mynetwork elasticsearch:6.6.1

docker run -p 5601:5601 --name kibana -d --network mynetwork kibana:6.6.1
docker run -d --network mynetwork --name logstash -p 5000:5000 logstash:6.6.1 -e 'input { tcp { port => 5000 codec => "json" } } output { elasticsearch { hosts => ["elasticsearch"] index => "micro-%{serviceName}"} }'
