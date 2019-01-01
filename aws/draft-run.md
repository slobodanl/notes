_Written by: Reza Shams Amiri_
# draft: setup serverless
Follwing [Serverless Framework - AWS Lambda Guide - Credentials][SFALGC]
1. Login page: [Logga in to AWS Management Console][LI]
2.  `Identity & Access Management (IAM)` page  `Users`  `Add user`
3. Enter a `name` in the first field, to remind you this User is the Framework, use like serverless-**agent**
    1. Enable `Programmatic access` by clicking the checkbox. Click `Next` to go through to the Permissions page
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