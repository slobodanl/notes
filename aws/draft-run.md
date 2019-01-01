_Written by: Reza Shams Amiri_
# draft: setup serverless
Follwing [Serverless Framework - AWS Lambda Guide - Credentials][SFALGC], to run [aws-python-rest-api-with-dynamodb][EAPRAWDAMSEG]: 

1. Login page: [Logga in to AWS Management Console][LI]
2.  `Identity & Access Management (IAM)` page  `Users`  `Add user`
3. Enter a `name` in the first field, to remind you this User is the Framework, use like serverless-**agent**
    1. Enable `Programmatic access` by clicking the checkbox. Click `Next` to go through to the Permissions page
    2. Click on `Attach existing policies directly`
    3. Click on `Create policy`.   
        ![create-policy.png](/img/aws/create-policy.png)
    4. Select the `JSON` tab, add the following JSON file you'll find in this [gist][MCSFSFG]  
        ![policy-json.png](/img/aws/policy-json.png)
    5. When you are finished, select `Review policy`
    6. Assign a name to the policy, like agent-**policy**
    7. Choose `Create Policy`
    8. Go back to the user creation page and click on the button below:  
        ![create-user-2.png](/img/aws/create-user-2.png)
    9. Click `Next: Tags`  `Next: Review`  `Next: Create user`
    10. You will endup on a page like this:  
        ![create-user-success.png](/img/aws/create-user-success.png)
1. Add the following lines to your `.bashrc`  
    ``` sh
    export AWS_ACCESS_KEY_ID=<your-key-here>
    export AWS_SECRET_ACCESS_KEY=<your-secret-key-here>
    ```
2. To deploy run:  
    ``` sh
    serverless deploy
    ```

# draft run

- Install yarn: [Installation | Yarn][IY]

``` sh
export PATH="$PATH:`yarn global bin`"
yarn install -g create-react-app

```

* * *
Creation date: _2018-12-26_

[LI]: https://sects.axis.com/adfs/ls/IdpInitiatedSignOn.aspx

[IY]: https://yarnpkg.com/en/docs/install#debian-stable
[SFALGC]: https://serverless.com/framework/docs/providers/aws/guide/credentials/?utm_source=cli&utm_medium=cli&utm_campaign=cli_helper_links
[MCSFSFG]: https://gist.github.com/ServerlessBot/7618156b8671840a539f405dea2704c8
[EAPRAWDAMSEG]: https://github.com/serverless/examples/tree/master/aws-python-rest-api-with-dynamodb