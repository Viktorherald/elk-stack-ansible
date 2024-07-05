# Installation Steps
Notes: Some dependency are continued from Elastisearch pre-requisite Step 1 - 3

1. Update apt repository, and install kibana - `sudo apt-get update && sudo apt-get install kibana`
2. Add elasticsearch enrollment token for kibana - `sudo /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana` <- Register output and paste to `/opt/data`
3. Amend config files - Change `#server.host: "localhost"` to `server.host: 0.0.0.0` in `/etc/kibana/kibana.yml`
4. Restart daemon and enable kibana.service - `sudo /bin/systemctl daemon-reload & sudo /bin/systemctl enable elasticsearch.service`, `sudo systemctl start kibana.service`

# Verification
1. Copy the enrollment token on ansible output
2. Navigate to `<box private ip>:5601`, 
3. Paste the enrollment token of kibana
4. Run `sudo /usr/share/kibana/bin/kibana-verification-code` in the box to get the verification code for the prompt
5. Key in Username and password