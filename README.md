# Log Monitoring with ELK Stack

# 📌  Goal

Implement centralized logging using Elasticsearch, Logstash, and Kibana (ELK) to collect, process, and visualize application logs efficiently.




## Tech Stack

**Elasticsearch:** Stores and indexes logs

**Logstash:** Processes and forwards logs

**Kibana:** Visualizes logs with dashboards

**Filebeat:**  Collects logs from applications

**Docker:**  Containerizes the ELK Stack


## Installation Steps

## 1️⃣ Install ELK Stack using Docker Compose

Ensure you have Docker and Docker Compose installed:



    sudo apt update && sudo apt install -y docker.io
    sudo apt install -y docker-compose


## Verify installation:



    docker --version
    docker-compose --version
  
## 2️⃣ Install ELK Stack Using Docker Compose
### Create a Project Directory


    mkdir elk-stack 
    cd elk-stack

 ### Create a docker-compose.yml File
 Define your ELK services inside this file.
 
    nano docker-compose.yml

### Create a Logstash Configuration File (logstash.conf)

    nano logstash.conf
    

 
    

### Start ELK Stack Using Docker Compose
    docker-compose up -d

### Check running containers:
    docker ps

    
### 3️⃣ Configure Filebeat to Collect Logs
#### Install Filebeat
    curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.17.9-linux-x86_64.tar.gz

    tar -xzf filebeat-7.179-linux-x86_64.tar.gz
    cd filebeat-7.17.9-linux-x86_64

 #### Edit Filebeat Configuration (filebeat.yml)

 ##### Edit this data in filebeats
    filebeat.inputs:
        - type: log
         enabled: true
         paths:
         - /var/log/*.log  # Change this to your application log path

    output.logstash:
    hosts: ["localhost:5044"]


##### Start Filebeat
    ./filebeat -e

![staticwebsite](image.png)

