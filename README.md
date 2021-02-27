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

## Priviledges 
### AWS IAM user dcreader 
```
key: AKIA3Y3FKCSIUOKBFYGT
```
read access to s3://digitalcorpora-logs/

### Dreamhost user `dcstats`


### Creamhost user `dcwriter`



# Configuration
.aws/config:
```
[default]
region = us-west-2
output = json
```
