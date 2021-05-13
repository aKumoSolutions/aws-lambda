## Manual Steps:

#### Step 1: Login to AWS Account 

* Login to ```AWS Account```
* Select the ```Region```

#### Step 2: Select Lambda Service

* Navigate to ```AWS Lambda```

#### Step 3: Create Function

* Click ```Create function``` button

- We are presented with 4 options:
    - ```Author from scratch```
    - ```Use a blueprint```
    - ```Container Image```
    - ```Browse serverless app repository```

#### Step 4:

* Select ```Author from scratch```
    - This is essentially building the function from scratch. 

* Fill out the Basic Information 
    - ```Function Name``` - name for the lambda function
        - Example: HelloWorld
    - ```Runtime``` - language you will be coding the function in
        - Example: Python 3.6

**Note**: For this example we will do the following: 
        - ```Function Name``` = HelloWorld
        - ```Runtime``` = Python 3.6

#### Step 5: Create Execution Role for Function

* Under ```Permission``` we have the options to select ```Execution Role``
    - We are presented with options:
        - ```Create a new role with basic Lambda permissions```
            - This option requires us to create an ```IAM Role```
        - ```Use an existing role```
            - This option gives us the ability to select an existing IAM Role for Lambda Execution
        - ```Create a new role from AWS policy templates```
            - This option requires ```Role name``` and we have the ability to select of one or more pre-defined templates

**Note**: For this example we will leave default ```Create a new role with basic Lambda permissions```

* Click ```Create funtion```

#### Step 6: Add/Modify Function Code

* The next page has a few sections
    - ```Function Overview```
    - ```Code source```
    - ```Code properties```
    - ```Runtime settings```
    - ```Layers```

* Under ```Code source``` we see a folder with function name and ```lambda_function.py```

* Select / Double Click on ```lambda_fucntion.py```

* Paste the following code

```
import json

def lambda_handler(event, context):
    # TODO implement
    print("message" + event['message'])
    
    return event['message'] # echo back the message(key) value
    raise Exception('Something went wrong!')
```

* Click on ```Deploy```

* Click on ```Test```
    - This opens ```Configure test event``` window
    
* Enter ```Event name```
    - ```Event name``` = Test

* Modify the ```json``` key value to following

```
{
    "message": "It worked! And 'Hello World'"
}
```

* Click ```Create```

**Note:** Now we are ready to test our function

#### Step 7: Invoke/Test Function 

* Under ```Code source``` click on ```Test``` 

**Note:** This generates an ```Execution result```. Under the ```Response``` we see "It worked! And 'Hello World" which is the value for the key "message". 

#### Step 8: Check Function Logs in CloudWatch

* We can check ```AWS CloudWatch``` for our function logs. 

* Navigate to ```CloudWatch```
    - Under ```Logs``` select ```Log groups```
    - Here we see a ```log group``` named ```/aws/lambda/HelloWorld```
    - Click on log group
        - Under ```Log streams``` we see stream generated
        - Click on the latest stream
            - Here we see ```Log events``` which includes 
                * ```START RequestId```
                * ```message``` - this is the value of key we defined in parameters
                * ```END RequestId```
                * ```REPORT```
