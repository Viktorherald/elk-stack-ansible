# Installation steps
Notes: 
- Some dependency are continued from Elastisearch pre-requisite Step 1 - 3
- VM to low memory might cause issues, i use 8GB RAM

1. Update apt repository, and install logstash - `sudo apt-get update && sudo apt-get install logstash`
2. Start Logstash service - `sudo systemctl start logstash.service`

# Verification steps
1. Run `sudo /usr/share/logstash/bin/logstash -e 'input { stdin { } } output { stdout {} }'`
2. When the terminal says ready to accept std input, enter any value will cause the logstash to return timestamp, indicating success.
