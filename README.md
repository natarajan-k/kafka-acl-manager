# Kafka ACL Manager
A Kafka Admin Client in Java to manage Kafka ACLs.   
If you are using IBM Event Streams, you can use the EventStreams portal to create RBAC.    
If you are using other Kafka - then, this could be used to create ACLs.    

## Pre-Req:

* You need to have a functioning Kafka (with KRaft) platform.    
* Java version at least 25. 

## Guide to Getting Started
1. Create a folder in your local laptop and change directory to that folder. 
2. Clone the repository.   
git clone https://github.com/natarajan-k/kafka-acl-manager.git.     
Alternatively, download the zip file inside the pre-compiled folder and unzip it locally.   
3. Update the acl.properties file. 

4. Test Creating ACLs. You can use the below examples as guide.   

## Examples.  

### List ACLs.  
    java -jar KafkaAclManager.jar --command list 

### Create ACLs
1. Producer: Write Access to ALL topics for user01.  

       java -jar KafkaAclManager.jar --command create --user user01 --topic ALL --operation WRITE

2. Producer: Write Access to one specific topic to user01.   

       java -jar KafkaAclManager.jar --command create --user user01 --topic topic1 --operation WRITE
       
3. Producer: Write Access to topics with a prefix 'order' to user01.

       java -jar KafkaAclManager.jar --command create --user user01 --topic order* --operation WRITE

4. Consumer: Read Access to All topics to user01 using consumer-group user01-group. 

       java -jar KafkaAclManager.jar --command create --user user01 --topic ALL --operation READ --group user01-group

5. Consumer: Read Access to one specific topic to user01 using any consumer-group.   

       java -jar KafkaAclManager.jar --command create --user user01 --topic topic1 --operation READ --group ALL

6. Both Producer and Consumer: Read and Write access to one specific topic to user01 using a specific consumer-group.

       java -jar KafkaAclManager.jar --command create --user user01 --topic topic1 --operation ALL --group user01-group

### Delete ACLs

1. Completely clear ALL ACLs. 

       java -jar KafkaAclManager.jar --command delete --user ALL --topic ALL

2. Delete all ACLs for a specific user.

       java -jar KafkaAclManager.jar --command delete --user user01 --topic ALL

3. Delete all users from a specific topic.

       java -jar KafkaAclManager.jar --command delete --user ALL --topic topic1

4. Delete one specific user from one specific topic.

       java -jar KafkaAclManager.jar --command delete --user user01 --topic topic1