#### laawsfords
#####5 Develop aws data processing
######Use firehose to load data into s3
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
######using kinesis in streaming solutions
workflow: s3->lambda for extract->kinesis->lambda for transform->kinesis->kinesis firehose->redshift
