# proyect-big-data-analytics
This repository contains information from the BigDataAnalytics project! Welcome

## Uso de MapReduce 
### punto 1 ¿Qué resultados generó el programa y cuales son los pasos MapReduce que implementa?

Como resultado se obtiene el log con la ejecución de los pasos de MapReaduce.

![image](https://user-images.githubusercontent.com/79612461/133517654-6819c86b-e3af-40bd-86a6-d2040fb230d4.png)

### Pasos de MapReduce
1. Una vez se ejecuta el programa MapReduce sobre un conjunto de ficheros guardados en el HDFS, se inicia el proceso de Stage Map donde el metodo JobResourceUploader desabilita la codificación de borrado del directorio output; luego procesa los datos con mapper y los distribuye en conjutos de datos mas pequeños.
2. Luego se inicia el proceso de shuffle donde por medio de la función jobSubmitter genera un token de trabajo y copia los datos en todos los nodos del cluster (dataNode) con el detalle de la tarea a realizar conforme a parametro de entrada.  
3. Por ultimo, se inicia la etapa ruduce por medio de la función Job, esta toma los datos que llegan del stage map, los combina y genera un nuevo conjunto de datos. Al finalizar la trabajo asignado, se recopilan los datos y lo envian de vuelta al servidor hadoop.

![image](https://user-images.githubusercontent.com/79612461/133502005-d65de1a2-6b08-4777-9a79-b66e82f7587e.png)

## punto 2 workcount ¿Qué resultados generó el programa y cuales son los pasos MapReduce que implementa?

Como resultados de ejecutar los siguientes pasos, se obtiene el conteo de palabras con uso de algoritmo wordcount de MapReduce:

### Ejecución de algoritmo wordcount en archivo ubicado en directorio libros
```
hadoop jar hadoop-mapreduce-examples-3.3.1.jar wordcount /libros /output-libros
```
![image](https://user-images.githubusercontent.com/79612461/133526655-b3ccdd19-a968-4644-aad1-8ed769dc9f83.png)

### Busqueda de conjunto de datos en directorio output-libros generados despues de ejecutar pasos de MapReduce
```
hdfs dfs -ls /output-libros
```
![image](https://user-images.githubusercontent.com/79612461/133527183-63c4a8dc-be7b-45ad-bd83-9f9d4deafa33.png)

![image](https://user-images.githubusercontent.com/79612461/133527095-0c46a9b8-2f73-4218-be6a-f529b5120720.png)

### Descarga de resultado 
```
hdfs dfs -get /output-libros/part-r-00000
```
![image](https://user-images.githubusercontent.com/79612461/133526998-07a74758-1968-4942-bc81-1d3a0b63a0b1.png)

### Visualización de nuevo conjunto de datos generados 
```
cat part-r-00000
```
![image](https://user-images.githubusercontent.com/79612461/133527049-8e31dae7-12f2-4c1b-be8a-44a9bf2b58c8.png)

## Uso de Spark 
### 









## punto 4

# Instalaciones

## Instalación entorno de virtualización Windows

### Ejecutar cmd como administrador
![image](https://user-images.githubusercontent.com/79612461/133538210-a1ade41b-9995-4998-9124-658175ecb6a3.png)

```
wsl --install
```
![image](https://user-images.githubusercontent.com/79612461/133538069-ce1fdc32-ee5c-4cd6-8a3c-f43384c40152.png)

## Instalación entorno virtual ubuntu

Abrir Microsoft Store buscar Ubuntu e instalar Ubuntu 20.04 LTS (no se requiere iniciar sesión)

![image](https://user-images.githubusercontent.com/79612461/133538345-eb3165a6-a610-44c1-837c-194215d0b4c7.png)

### Configuración archivo .wslconfig

Ir a la ruta del usuario
```
C:\Users\<user>
```
Crear archivo con el nombre .wslconfig (eliminar extensión .txt y confirmar que el archivo no tiene extensión) 

![image](https://user-images.githubusercontent.com/79612461/133538633-e68aedba-7814-4bf2-91ca-18448f7383b5.png)

Dentro del archivo .wslconfig copiar 
```
[wsl2]
memory=4GB
processors=2
localhostForwarding=true
```
![image](https://user-images.githubusercontent.com/79612461/133538769-1bf96548-b0b1-4e45-8ebd-b79b2ba49fc8.png)

### NOTA: La etiqueta memory puede variar entre 2GB y 4GB

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
![image](https://user-images.githubusercontent.com/79612461/133352393-f42bee21-0d34-41b8-b3b2-2fa58fcd1c44.png)
![image](https://user-images.githubusercontent.com/79612461/133352354-f4eaad0b-fab0-48de-9fc8-12f6eaab49ca.png)


## Instalacion Spark (parte 3)
```
sudo apt install scala git -y
java -version; javac -version; scala -version; git --version
```
![image](https://user-images.githubusercontent.com/79612461/133352999-611b31d3-6a3b-4494-820e-07e22516d725.png)
![image](https://user-images.githubusercontent.com/79612461/133353057-2db191f9-d1d6-4721-ba8b-6616eac7032e.png)

### Ingresar y descargar la ultima versión con el comando wget

https://spark.apache.org/downloads.html
```
wget https://downloads.apache.org/spark/spark-<version>/spark-<version>-bin-hadoop3.2.tgz
```
![image](https://user-images.githubusercontent.com/79612461/133353128-74aff860-682e-4d29-ac27-c045d00853bd.png)
```
tar xvf spark-<version>.tar.gz
```
![image](https://user-images.githubusercontent.com/79612461/133353193-a02133c9-66b9-48fb-8737-7b3f7bbb33ff.png)

```
sudo mv spark-<version>-bin-hadoop2.7 /opt/spark
which python3
```
![image](https://user-images.githubusercontent.com/79612461/133353358-09e6ae85-c8a8-47a9-a0f2-c80e8386c5ee.png)

```
nano .profile
```
![image](https://user-images.githubusercontent.com/79612461/133353440-392e152f-cbcb-49ee-ab6d-afccb32bd482.png)
```
source ~/.profile
```
### Inicializar spark
```
start-master.sh
```
![image](https://user-images.githubusercontent.com/79612461/133353596-a5b0c3c1-ce3b-477c-b07e-048f8166f39e.png)
![image](https://user-images.githubusercontent.com/79612461/133353636-548cf7a3-a2e4-4c4c-bccf-45043afb8fa1.png)

### Inicialiación servidores esclavo
```
start-worker.sh spark://LAP-WIN-01166.localdomain:7077
```
![image](https://user-images.githubusercontent.com/79612461/133361341-87b26a27-9a0b-4d97-90ef-f10d652b4125.png)
![image](https://user-images.githubusercontent.com/79612461/133361420-ea8744d6-01a8-49fc-9577-c81ea7fc10a9.png)

## Instalación Anaconda 
```
wget https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh
bash Anaconda3-2021.05-Linux-x86_64.sh
```
![image](https://user-images.githubusercontent.com/79612461/133535276-c53439b0-0bbe-4ecf-8301-780f5a62b529.png)

## Instalación Jupyter
```
sudo apt install jupyter-core
```

![image](https://user-images.githubusercontent.com/79612461/133535992-a54eba73-fcc7-4582-a178-4e519d85ce32.png)
