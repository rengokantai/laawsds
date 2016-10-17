# laawsds

##3. Develop the AWS Website
###8 Use Elastic Beanstalk for website hosting
####00:50
Node.js -Launch now

####04:05
default website

####04:25
configuration ->auto scaling




###9 Apply Docker for website hosting
####02:43  
create a server: environment type  
Predifined configuration: multi-container Docker  
Environment type: Load balancing, auto scaling  

####04:00
Deployment preferences:
Rolling is default so what this means is that when you're Deploying as it says you can avoid downtime.  

####06:40
Environment tags  
myenv:dev

###10 Tip: The best mix of compute services for your website














##4. Develop the AWS Data Warehouse
###1 Why use a data warehouse
####00:40
A data warehouse is a method of storing your data in a way that's optimized for reading.  
And in sort of the old world of data you really just had what's called OLTP transactional processing and OLAP or OLAP analytical processing.  
Def:
- OLTP (On-line Transaction Processing) is characterized by a large number of short on-line transactions (INSERT, UPDATE, DELETE). The main emphasis for OLTP systems is put on very fast query processing, maintaining data integrity in multi-access environments and an effectiveness measured by number of transactions per second. In OLTP database there is detailed and current data, and schema used to store transactional databases is the entity model (usually 3NF). 

- OLAP (On-line Analytical Processing) is characterized by relatively low volume of transactions. Queries are often very complex and involve aggregations. For OLAP systems a response time is an effectiveness measure. OLAP applications are widely used by Data Mining techniques. In OLAP database there is aggregated, historical data, stored in multi-dimensional schemas (usually star schema). 


AWS big data options:  
files -> S3, glacier  
RDBMS -> Redshift(reads), Aurora(writes)  
Hadoop ->EMR

####05:17
Databases that are optimized for inserts, updates and deletes are row-stores.
####05:33
Databases that are optimized for reading are very often now optimized in columns rather than rows. So common optimization technique for relational databases is indexes and indexes is just copying the information from one or more columns of the database. Column store really just executes on this fully in that every single value in the database is organized by columns.




###3 Use Redshift
####04:08
Add sg:inbound rule:  
Redshift->source:MyIP


###4 Load your Redshift with data
####05:27
review syntax
```
copy tbname from 's3://bkname/a/tbname' credentials 'aws_access_key_id=AK123;aws_secret_access_key=123' 
gzip compupdate region 'us-west-2';
```
####08:20
clusters->last but 2 tab loads->check loads








##5. Develop aws data processing
###Use firehose to load data into s3
```
aws firehose describe-delivery-stream --delivery-stream-name ke --region us-east-1
```
put a record
```
aws firehose put-record --delivery-stream-name ke --record Data=123 --region us-east-1
```
batch
```
aws firehose put-record-batch --delivery-stream-name ke --record a b c --region us-east-1
```
wait 5 min.
###using kinesis in streaming solutions
workflow: s3->lambda for extract->kinesis->lambda for transform->kinesis->kinesis firehose->redshift

##6 Develop AWS IoT Project
###Use AWS IoT MQTT
step1: Device gateway connection:  
IOT->MQTT Client->create connectionID:ke,  
step2: subscribe to topic  
subsciption topic: \topic\today->  
max message capture:100->  
qos:0  
step3: publish to topic  
publish topic: \topic\today ->  
payload: ke

###Use IOT certificates and policies to secure device messages
