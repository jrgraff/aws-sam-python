Require: SAM CLI, Python3, Docker

# build your application locally using a container
 sam build --use-container

 # deploy your application to the AWS cloud 
 sam deploy --guided

 # generate a synthetic event
 sam local generate-event

 # invoke a Lambda function locally
 sam local invoke PythonTestDemo --event events/event.json

 # start a local emulator for a Lambda function endpoint
 sam local start-lambda --region us-east-1

 # run a unit test in a separate terminal
 python3 -m pytest -s tests/unit/local_emulator_test.py -v

 # start a local emulator for an API Gateway endpoint
 sam local start-api

 # make a request to the endpoint in a separate terminal
 curl http://localhost:3000/hello

 # Create and Activate a Python Virtual Environment
 pip3 install virtualenv
 python3 -m venv venv
 source ./venv/bin/activate

# install dependencies
 pip3 install -r tests/requirements.txt

# run unit tests with mocks
 python3 -m pytest -s tests/unit/mock_test.py -v

 # Set the environment variable AWS_SAM_STACK_NAME to the name of the stack you specified during deploy
 AWS_SAM_STACK_NAME=<stack-name> python3 -m pytest -s tests/integration -v

 # invoke a Lambda function in the cloud using the AWS CLI.  Substitute the function name as created in your stack.
 aws lambda invoke --function-name apigw-lambda-PythonTestDemo-6Ecinx8IauZv outfile.txt

 # synchronize local code with the cloud
 sam sync --watch --stack-name apigw-lambda

 # list logs
 sam logs -n PythonTestDemo --stack-name apigw-lambda --tail

 # cleanup
 aws cloudformation delete-stack --stack-name apigw-lambda