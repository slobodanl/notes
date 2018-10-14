_Written by: Reza Shams Amiri_
# PluralSight: AWS big picture

1. What is AWS
    1. EC2 (Elastic Cloud Computing)
        1. Creating an instance

# EC2
## Creating an instance and connecting to the instance
1. Goto the console and create an instance
2. Install AWS tools ([][AI])
3. Get the ID of the instance ([][CTYLIUSAECC])
4. Use ssh to connect to the instance  
    ``` sh
    tsocks ssh -i "reza.pem" ubuntu@ec2-18-224-95-164.us-east-2.compute.amazonaws.com
    ```
    **`reza.pem`, is the created key for the account  
    `tsocks`, is required to bypass the proxy**{.info}

There are costs associated with instances you can see the costs:
* * *
Creation date: _2018/10/11_

[AI]: /1-CSI/1.1-user-services/team-space/Reza/aws/aws-information
[CTYLIUSAECC]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html