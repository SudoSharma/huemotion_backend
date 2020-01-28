# Huemotion Backend

## Overview

This is the lambda function code for a progressive web app which predicts emotions in real-time using a serverless architecture.

Images are captured from a web cam and sent to an AWS Lambda function which serves an inference model for facial expression recognition. The model is stored using the [Open Neural Network Exchange (ONNX)](https://github.com/onnx/onnx), an open standard format for representing machine learning models. 

## Instructions to Replicate

1. Create an Amazon EC2 instance using an [AWS Lambda Runtime Image](https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtimes.html). This will mimic the AWS Lambda environment and the correct versions of packages/binaries will be compiled appropriately. 
2. In that instance, clone this repository, and **inside the repository** create a virtual environment using virtualenv: `python -m venv $MYENV`, replacing `$MYENV` with whatever you'd like to call this environment. It's important that the virtual environment be created inside this repository folder to help Zappa function properly. 
3. Install app requirements: `pip install -r requirements.txt`. 
4. Setup your [AWS configurations](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html). 
5. Edit the `get_emotions.py` script to point to an S3 bucket where you've stored your own ONNX model, or stick with the model I've currently deployed (you'll have read-only access).  
6. Setup and deploy to AWS Lambda using [Zappa](https://github.com/Miserlou/Zappa), which was installed along with all other app requirements earlier, and which will setup all the configurations to create a proper API endpoint. Example Zappa settings are included in this repository for your reference. **Be sure to change this with your own configuration details or delete it all together before running `zappa init`.**
7. Test the endpoint by sending an img using an encoding type of [`"multipart/form-data"`](https://developer.mozilla.org/en-US/docs/Web/API/FormData). You can see an example of this in the [front-end repository](
https://github.com/SudoSharma/huemotion) for this application. 

## App URL

https://huemotion.sudosharma.com

## Suggestions

Please feel free to suggest improvements by filing an issue, or creating a pull request.
