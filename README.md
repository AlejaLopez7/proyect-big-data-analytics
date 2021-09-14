# proyect-big-data-analytics
This repository contains information from the BigDataAnalytics project! Welcome

## Instalación de ubuntu

## Creación de usurio hadoop en ubuntu
![image](https://user-images.githubusercontent.com/79612461/133336179-8d141879-3d21-4270-80ef-67dc5b7ad0d7.png)
## Instalación de jdk en ubuntu
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

## Configuración ssh y llave cifrada
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

##
