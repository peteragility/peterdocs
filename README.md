# Peter Working Tips

## Nice Articles
* https://aws.amazon.com/blogs/media/top-10-things-to-consider-when-migrating-your-vod-library-to-aws/
* https://medium.com/debugging-aws-lambda-functions-from-eclipse-with/debugging-aws-lambda-python-function-with-eclipse-using-pydev-1e0fa4b2deff
* https://medium.com/swlh/hacking-json-web-tokens-jwts-9122efe91e4a

## Amazon Rekognition
List Rekognition collections
```
aws rekognition list-collections
```
Create a Rekognition collection
```
aws rekognition create-collection --collection-id "faces" --region ap-southeast-1
```
Train the collection with images in S3
```
aws rekognition index-faces \
--image '{"S3Object":{"Bucket":"samsung-aisage", "Name":"images/peterchan-face-2.jpg"}}' \
--collection-id 'faces' --max-faces 1 --quality-filter 'AUTO' --detection-attributes 'ALL' --external-image-id 'peterchan' --region ap-southeast-1
```
Delete a Rekognition collection 
```
aws rekognition delete-collection --collection-id "faces"
```
List faces in a collection
```
aws rekognition list-faces --collection-id "collection-id"  
```
Delete faces in a collection
```
aws rekognition delete-faces --collection-id "collectionname" --face-ids '["faceid"]'
```

## SAM Cheatsheet
Init a sample SAM project
```
sam init --runtime python3.7 -n hello_world
sam init --runtime java8 -n hello_world_java
```
To build on your workstation, run this command in folder containing SAM template. Built artifacts will be written to .aws-sam/build folder
```
sam build
``` 
To build inside a AWS Lambda like Docker container
```
sam build --use-container
```
To build and package for deployment
```
sam build && sam package --s3-bucket <bucketname>
```
Invoke lambda locally once, will be launched in a docker
```
sam local invoke
sam lcoal invoke <functionName> --event testEvent.json
```
Start local API for debugging
```
sam local start-api
```
Guided SAM deployment to AWS
```
sam deploy -g
```
Package an application
```
sam package --template-file template.yaml --output-template-file packaged.yaml --s3-bucket samsung-aisage
```
Publish an application
```
sam publish --template packaged.yaml --region ap-southeast-1
```
## Python Cheatsheet
Run a python file/module
```
python app.py
python -c 'from app import lambda_handler; lambda_handler()'
```
Install package using pip
```
pip install <package>
sudo pip install <package>
```
Create a virtual environment
```
virtualenv v-env
```
Activate the virtual environment
```
source v-env/bin/activate
```

## Git Cheatsheet
Compare changes with local branch
```
git diff
```
Add files to stage
```
git add <files>
```
Commit to local branch
```
git commit -m "message"
```
Push to remote branch
```
git push
```
Checkout branch
```
git checkout master
```
Git status
```
git status
```

## Linux commands
Find location of a executable
```bash
which python
```
