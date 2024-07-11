# Installation steps
1. Get the keyring from Elasticsearch - `wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg`
2. Install dependency package - `sudo apt update & sudo apt install apt-transport-https`
3. Save the repository definition - `echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list`
4. Update apt repository again, and install elasticsearch - `sudo apt-get update && sudo apt-get install elasticsearch` <- Register output and paste to `/opt/data`
5. Change Elasticsearch file permissions - `/etc/elasticsearch/` and `/etc/elasticsearch/certs` to 755, `/etc/elasticsearch/certs/http_ca.crt` to 444
6. Amend the network.host value - `sed -i 's|network.host: 192.168.0.1|network.host: 0.0.0.0|' /etc/elasticsearch/elasticsearch.yml`
7. Reload Daemon and enable elasticsearch service - `sudo /bin/systemctl daemon-reload & sudo /bin/systemctl enable elasticsearch.service`, `sudo systemctl start elasticsearch.service`

# Verification steps

1. On the Ansible output, copy the elastic user password.
2. SSH into the box, and `export ELASTIC_PASSWORD="<the password>"`
3. Run `curl --cacert /etc/elasticsearch/certs/http_ca.crt -u elastic:$ELASTIC_PASSWORD https://localhost:9200` to ensure a proper JSON response is obtained.
