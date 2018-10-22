_Written by: Reza Shams Amiri_

# 03 Lambdas
- Limitations  

| Resource Limitations |  |
| -------------------- | --- |
| Ephemeral ( temporary ) storage | < 512 MB |
| Maximum execution duration | < 300 Seconds |
| Concurrent Lambda functions | < 100 |

- Mitigations:  
    1. Load and store files in S3
    2. Chain functions together
    3. Ask for increasing limits
- Considerations:
    1. Event driven code
    2. Code size limitations
    3. Lambda as a component
    4. Performance limitations (1.5 GB Memory)

1. 


- - -

Creation date: _2018/10/22_