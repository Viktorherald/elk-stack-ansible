# Basic usage on connecting Packetbeat directly to Elasticsearch

## Installation steps
Notes: 
- Some dependency are continued from Elastisearch pre-requisite Step 1 - 3

1. Update apt repository, and install logstash - `sudo apt-get update && sudo apt-get install packetbeat`
2. Start Packetbeat service on boot - `sudo systemctl enable packetbeat`

## Configuration outside Ansible
1. Configure connection information in `/etc/packetbeat/packetbeat.yml` file (Refer to [Step 2, 3](https://www.elastic.co/guide/en/beats/packetbeat/8.11/packetbeat-installation-configuration.html]), using username = elastic, and its password)
2. Setup assets and start Packetbeat (Refer to [Step 4, 5](https://www.elastic.co/guide/en/beats/packetbeat/8.11/packetbeat-installation-configuration.html]))

## Verification steps
1. Navigate to Elastic server with browser
2. Click Discover > `packetbeat-*` index pattern: <br>
![Alt text](image.png)
3. Set the filtering, trigger the ping from host machine, and verify that it is logged.<br>
![Alt text](image-1.png)