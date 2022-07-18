# ELK-AWS
Steps to deploy ELK stack on AWS EC2

## ElasticSearch
Use AWS Linux, T2 micro, existing key pair, limit IPs via SG.

### Complete install from download instrustions
```
https://www.elastic.co/guide/en/elasticsearch/reference/8.3/rpm.html#rpm-repo
```

### Base download
```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.3.2-x86_64.rpm
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.3.2-x86_64.rpm.sha512
sudo rpm --install elasticsearch-8.3.2-x86_64.rpm
```

The generated password for the elastic built-in superuser is : rhgFW1KSVg0kVpj*-4yH

If this node should join an existing cluster, you can reconfigure this with
'/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token-here>'
after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with
'/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with
 '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'.

Generate an enrollment token for Elasticsearch nodes with
'/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node'.

### Run with systemd
systemctl daemon-reload
systemctl enable elasticsearch.service
### You can start elasticsearch service by executing
systemctl start elasticsearch.service

### Validate your install is running
```
curl --cacert /etc/elasticsearch/certs/http_ca.crt -u elastic https://localhost:9200
```
