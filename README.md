# Using S3 Lifecycle Policies to Reduce Storage Costs
## Preparation
### Set a unique suffix to use for the S3 bucket name:
```
RANDOM_STRING=$(aws secretsmanager get-random-password \
--exclude-punctuation --exclude-uppercase \
--password-length 6 --require-each-included-type \
--output text \
--query RandomPassword)
```

### Create S3 bucket:

`aws s3api create-bucket --bucket awsboswell-$RANDOM_STRING`



## Clean up 
### Delete the file you copied to your S3 bucket:

`aws s3 rm s3://awsboswell-$RANDOM_STRING/book_cover.png`

### Delete the S3 bucket:

`aws s3api delete-bucket --bucket awsboswell-$RANDOM_STRING`

### Unset the environment variable that you created manually:

`unset RANDOM_STRING`
