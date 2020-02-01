# Peter Working Tips

## Media Vertical Reads
* https://aws.amazon.com/blogs/media/top-10-things-to-consider-when-migrating-your-vod-library-to-aws/

## Cloudformation and SAM
* https://medium.com/debugging-aws-lambda-functions-from-eclipse-with/debugging-aws-lambda-python-function-with-eclipse-using-pydev-1e0fa4b2deff

## SAM Cheatsheet
Init a sample SAM project
```
sam init --runtime python3.7 -n hello_world
```
Build using container
```
sam build –use-container
```
Invoke lambda locally which will be run in local docker
```
sam local invoke
sam lcoal invoke <functionName> --event testEvent.json
```
Guide SAM deployment to AWS
```
sam deploy -g
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
