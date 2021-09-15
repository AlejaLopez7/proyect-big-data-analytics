# proyect-big-data-analytics
This repository contains information from the BigDataAnalytics project! Welcome

## Instalación de ubuntu (base)

### Creación de usurio hadoop en ubuntu
![image](https://user-images.githubusercontent.com/79612461/133336179-8d141879-3d21-4270-80ef-67dc5b7ad0d7.png)
### Instalación de jdk en ubuntu
```
sudo apt update
```
![image](https://user-images.githubusercontent.com/79612461/133345186-914ed15e-0e3e-4a71-a708-db4832dc29b0.png)
![image](https://user-images.githubusercontent.com/79612461/133345206-740085e2-cf67-42bb-8060-405f0556adec.png)
```
sudo apt install openjdk-8-jdk -y
```
![image](https://user-images.githubusercontent.com/79612461/133345306-db8e2b7e-ab95-455e-a8e2-54bb08238f07.png)
![image](https://user-images.githubusercontent.com/79612461/133345325-a5d0d5ac-54a0-4588-9a0f-4a8047cfd141.png)

```
java -version; javac -version
```
![image](https://user-images.githubusercontent.com/79612461/133345356-8a8e38d0-3eac-419b-aae8-adca713e296a.png)

### Configuración ssh y llave cifrada
```
sudo apt install openssh-server openssh-client -y
```
![image](https://user-images.githubusercontent.com/79612461/133345678-21132d86-0bfd-4f4a-ab7f-1a7b3239233a.png)
```
ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
```
![image](https://user-images.githubusercontent.com/79612461/133345796-af327641-7c1e-4682-9923-961eae65a809.png)
```
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
```
```
chmod 0600 ~/.ssh/authorized_keys
```
```
ssh localhost
```
![image](https://user-images.githubusercontent.com/79612461/133346100-32d5390b-91a1-430c-b455-d944448e5117.png)
```
service ssh restart
```
```
sudo apt-get remove openssh-client openssh-server
```
![image](https://user-images.githubusercontent.com/79612461/133346524-73f2fceb-d5f8-4f2e-bac0-260b504556c7.png)
```
sudo apt-get install openssh-client openssh-server
```
![image](https://user-images.githubusercontent.com/79612461/133346611-30acdd2e-6b35-43ea-9cf2-0daac0d485e0.png)
```
sudo service ssh restart
```
![image](https://user-images.githubusercontent.com/79612461/133346738-b0f995ae-504d-4f38-9288-9756a8b9bba8.png)
```
ssh localhost
```
![image](https://user-images.githubusercontent.com/79612461/133346823-2f91b4e8-b7c3-47f6-bda5-99e0afab55df.png)
```
ssh localhost
```
## Instalación de hadoop (parte 1)
### Ingresar y descargar la ultima version con el comando wget
![image](https://user-images.githubusercontent.com/79612461/133347168-b7348919-9ac1-48ab-a701-91024c862155.png)
![image](https://user-images.githubusercontent.com/79612461/133347174-d8fe0eec-cb8d-4ce6-a345-5d9712f1a2ae.png)
```
wget https://dlcdn.apache.org/hadoop/common/hadoop-<version>/hadoop-<version>.tar.gz
```
![image](https://user-images.githubusercontent.com/79612461/133347317-3a2463a3-586b-4731-9ad0-576056ed2749.png)
```
tar xzf hadoop-<version>.tar.gz
```
![image](https://user-images.githubusercontent.com/79612461/133347478-e6ff93a5-b6cb-42e3-b726-375797534364.png)
```
mv hadoop-<version> hadoop
```
### Implementación de Hadoop de nodo único
```
sudo nano .bashrc
```
![image](https://user-images.githubusercontent.com/79612461/133347894-71f237bc-857e-41df-868a-4b58ae04284f.png)
```
source ~/.bashrc
```
```
sudo nano $HADOOP_HOME/etc/hadoop/hadoop-env.sh
```
![image](https://user-images.githubusercontent.com/79612461/133348046-3936b827-6c99-4c8d-8451-7a3676770b66.png)
```
cd hadoop
mkdir tmpdata
chmod 777 tmpdata
```
![image](https://user-images.githubusercontent.com/79612461/133348269-acf90553-48af-427a-abad-eaef683d162e.png)
```
sudo nano $HADOOP_HOME/etc/hadoop/core-site.xml
```
![image](https://user-images.githubusercontent.com/79612461/133348565-1fc922a7-2c13-42aa-a6ff-8d320dba67f0.png)

```
mkdir -p ~/hadoopdata/hdfs/namenode
mkdir -p ~/hadoopdata/hdfs/datanode
```
```
sudo nano $HADOOP_HOME/etc/hadoop/hdfs-site.xml
```
![image](https://user-images.githubusercontent.com/79612461/133348767-f8f79844-1f48-46d2-96d9-677867191ef2.png)

```
sudo nano $HADOOP_HOME/etc/hadoop/mapred-site.xml
```
![image](https://user-images.githubusercontent.com/79612461/133348863-dcefa798-5fae-454e-bbce-c0f8f5a54071.png)

### Modificación archivo yarn
```
sudo nano $HADOOP_HOME/etc/hadoop/yarn-site.xml
```
![image](https://user-images.githubusercontent.com/79612461/133349065-69d09316-96ff-47e1-8b71-0bb03c61eec7.png)

### Format HDFS NameNode
```
hdfs namenode -format
```
![image](https://user-images.githubusercontent.com/79612461/133349245-fded655a-b572-40c6-bec8-31d978796bae.png)
![image](https://user-images.githubusercontent.com/79612461/133349335-ee1e79eb-542f-4d78-8c07-337df12f7dc9.png)

```
start-dfs.sh
start-yarn.sh
jps
```
![image](https://user-images.githubusercontent.com/79612461/133349579-3512de8e-56f5-4090-9463-cd5636dc324a.png)

### Acceso a Hadoop UI por medio del navegador de Windows
```
http://localhost:9870
```
![image](https://user-images.githubusercontent.com/79612461/133349750-0012e914-a27d-46fd-be67-2f60d0b2115a.png)
![image](https://user-images.githubusercontent.com/79612461/133349825-5293c7fa-dcab-49dc-b536-edaf555d8c67.png)

## Instalación de mapreduce (parte 2)
```
cd hadoop
bin/hdfs dfs -mkdir /user
bin/hdfs dfs -mkdir /user/<username>
bin/hdfs dfs -mkdir input
bin/hdfs dfs -put etc/hadoop/*.xml input
```
```
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.3.1.jar grep input output 'dfs[a-z.]+'
```
```
```
```
```
``````
```
```
```
```


## Instalacion Spark (parte 3)



```
```
```
```
```
```


