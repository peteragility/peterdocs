# Peter Working Tips

## Linux commands
Find location of a executable
```bash
which python
```
Find running networking ports
```bash
netstat -lptu
netstat -lpntu
```
Find running processes
```bash
ps aux | grep processName
```
### Run network throughput test (iperf)
Install iperf3
```
sudo yum install iperf3
```
Run iperf server
```
iperf3 -s
iperf3 -s -D
```
Run iperf client
```
iperf3 -c targetIP
iperf3 -c targetIP -t timeInSeconds
```

## AWS CLI Cheatsheet
Install AWS CLI 2 (Linux)
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
```
unzip awscliv2.zip
```
```
sudo ./aws/install
```
Edit credentials and config
```
vi ~/.aws/credentials
vi ~/.aws/config
```
Switch AWS Profile
```
export AWS_PROFILE=user1
```
S3 sync data
```
aws s3 sync . s3://bucketName/prefix --region ap-east-1
```
S3 delete data
```
aw s3 rm s3://bucketName/prefix --recursive --region ap-east-1
```

##  CDK / SAM Cheatsheet
Init a sample CDK project
```
cdk init sample-app --language java
cdk init sample-app --language python
```
Generate SAM template yaml from cdk
```
cdk synth --no-staging > lambda/template.yaml
```
Init a sample SAM project
```
sam init --runtime nodejs12.x -n hello_world
sam init --runtime python3.7 -n hello_world
sam init --runtime java8 -n hello_world
```
To build on your workstation, run this command in folder containing SAM template. Built artifacts will be written to .aws-sam/build folder
```
sam build
sam build --use-container
```
Invoke lambda locally in a docker, with event json
```
sam local invoke <functionName> --event testEvent.json
```
Start local API for debugging
```
sam local start-api
```
Package an application
```
sam build && sam package --s3-bucket <bucketname>
sam package --template-file template.yaml --output-template-file packaged.yaml --s3-bucket samsung-aisage
```
Publish an application
```
sam publish --template packaged.yaml --region ap-southeast-1
```
Guided SAM deployment to AWS
```
sam deploy -g
```

## K8S/EKS Cheatsheet
Install kubectl (1.16)
```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.16.8/2020-04-16/bin/linux/amd64/kubectl
```
```
chmod +x ./kubectl
```
```
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
```
```
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
```
```
kubectl version --short --client
```
Use the AWS CLI update-kubeconfig command to create or update your kubeconfig for your cluster
```
aws eks --region region_code update-kubeconfig --name cluster_name
```
Test the config
```
kubectl get svc
```
Scale a deployment
```
kubectl scale deployment.apps/nginx-deployment --replicas=10 -n <namespace>
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
```
Create a virtual environment in python 2, pls install virtualenv via pip first
```
virtualenv v-env
```
Create a virtual environment in python 3, the function is built in
```
python -m venv v-env
```
Activate the virtual environment
```
source v-env/bin/activate
```
### OpenCV Cheatsheet
Install opencv library for c++/python
```
sudo apt-get install python-opencv
```
Install Linux based video camera tool guvcview
```
sudo apt-get install guvcview
```
Check if a process using V4L resources
```
sudo lsof | grep libv4l2
```
List all virtual video devices
```
ls -l /dev/video*
```

## Amazon Rekognition
Create a Rekognition collection
```
aws rekognition create-collection --collection-id "test-collection" --region us-west-2
```
Index face image in S3 into a collection
```
aws rekognition index-faces --image '{"S3Object":{"Bucket":"test-bucket", "Name":"test.jpg"}}' --collection-id 'test-collection' --max-faces 1 --quality-filter 'AUTO' --detection-attributes 'ALL' --external-image-id 'testperson' --region us-west-2
```
List faces in a collection
```
aws rekognition list-faces --collection-id "test-collection" "face1-id" "face2-id" --region us-west-2
```
Search face by image (face match)
```
aws rekognition search-faces-by-image --image '{"S3Object":{"Bucket":"test-bucket", "Name":"someone.png"}}' --collection-id "test-collection" --max-faces 1 --quality-filter "AUTO" --region us-west-2
```

## Git Cheatsheet
Compare diff between modified/staged files with HEAD
```
git diff
git diff --cached
```
Add files to stage
```
git add .
git add -A
git add -u
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