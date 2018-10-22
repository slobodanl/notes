_Written by: Reza Shams Amiri_
# AWS information

1. Login page: [Logga in to AWS Management Console][LI]
2. Install prerequsites:
    1. Install the `AWS Command Line` [][ITACLIACLI]
        ``` sh
        pip install awscli --upgrade --user
        pip install awscli --upgrade --user
        aws --version
        ```
        
        _the files might be installed in `~/.local/bin/` make sure that it's in the PATH_{.note .yellow}
    1. Opening **port 80** on the instance:
        > - Go to the `Network & Security` -> `Security Group` settings in the left hand navigation
        > - Find the Security Group that your instance is apart of Click on `Inbound Rules`
        > - Use the drop down and add HTTP (port 80), click Apply
        
    1. Amazon Policy Generator [AWS Policy Generator][APG]

* * *
Creation date: _2018/10/11_

[LI]: https://sects.axis.com/adfs/ls/IdpInitiatedSignOn.aspx
[ITACLIACLI]: https://docs.aws.amazon.com/cli/latest/userguide/installing.html
[APG]: https://awspolicygen.s3.amazonaws.com/policygen.html