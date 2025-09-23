

# SPARK  INTEGRATION GUIDE 
# Update
sudo apt update && apt upgrade -y  

# get file
sudo apt install default-jdk curl -y  
wget https://dlcdn.apache.org/spark/spark-3.5.6/spark-3.5.6-bin-hadoop3.tgz  
tar -xzvf spark-3.5.6-bin-hadoop3.tgz  

sudo mv spark-3.5.6-bin-hadoop3 /opt/spark  
nano ~/.bashrc  
export SPARK_HOME=/opt/spark  
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin  
source ~/.bashrc  
useradd spark  
chown -R spark:spark /opt/spark  
nano /etc/systemd/system/spark-master.service  

[Unit]  
Description=Apache Spark Master  
After=network.target  

[Service]  
Type=forking  
User=spark  
Group=spark  
ExecStart=/opt/spark/sbin/start-master.sh  
ExecStop=/opt/spark/sbin/stop-master.sh  

[Install]  
WantedBy=multi-user.target  
nano /etc/systemd/system/spark-slave.service  


[Unit]  
Description=Apache Spark Slave  
After=network.target  

[Service]  
Type=forking  
User=spark  
Group=spark  
ExecStart=/opt/spark/sbin/start-slave.sh spark://your-server-ip:7077  
ExecStop=/opt/spark/sbin/stop-slave.sh  

[Install]  
WantedBy=multi-user.target  
systemctl daemon-reload  
systemctl start spark-master  
systemctl enable spark-master  
systemctl status spark-master  
systemctl start spark-slave  
systemctl enable spark-slave  
systemctl status spark-slave  
spark-shell



