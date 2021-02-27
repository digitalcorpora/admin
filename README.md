# Security Plan
## Assets
Information assets:
* Corpora in s3://digitalcorpora/
* Logs in s3://digitalcorpora-logs/
* MySQL database used for Wordpress
* MySQL database used for storing hashes.
* Wordpress .php installation

Code assets:
* https://github.com/digitalcorpora/security
* https://github.com/digitalcorpora/digitalcorpora-stats
* https://github.com/digitalcorpora/app
* https://github.com/digitalcorpora/open-data-registry

## AWS Priviledges 

|IAM User|Groups|Purpose|
|--------|------|-------|
|dcadmin |dcadmin-group  |       |
|dcreader|dcreader-group| Not sure; s3 bucket is wide open|
|dcwriter|dcwriter-group|Writing to s3://digitalcorpora/ |
|dclogger|dcloger-group|

IAM user dcreader  
```
key: AKIA3Y3FKCSIUOKBFYGT
```
read access to s3://digitalcorpora-logs/

## Dreamhost Priviledges
### Dreamhost user `dcstats`
Puprose: User that runs the https://downloads.digitalcorpora.org/ website and displays the real time states.
Requires:
* Anonymous access to s3://digitalcorpora/ bucket (everybody has hits)
* Read-only access to mysql database (so that it can display the stats)


### Dreamhost user `dclogs`
Purpose: every 5 minutes, ingests new logs from S3 bucket and deletes them
* Has access to AWS IAM user dclogger (which can read  and delete logfiles but not the primary bucket.)
* Has access to mysql user dclogger (which can select and insert on the database)
* Reads s3://digitalcorpora-logs/ and adds to the database



# Configuration
.aws/config:
```
[default]
region = us-west-2
output = json
```
