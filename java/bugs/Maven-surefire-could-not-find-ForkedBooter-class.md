_Written by: Reza Shams Amiri_
# [Maven surefire could not find ForkedBooter class][HSCQ5MSCNFFCN1L1]

This is a bug due to [openjdk-8-jdk: Maven surefire crashes after update to 8u181-b13-2][HBDO9]

See the following workarounds: [jira-issue][HIAOJBS1F1PCAJPSI3TC1], [stack-overflow-answer][HSCA51]

or simply add the following profile to your maven settings:
``` xml
<profile>
    <id>SUREFIRE-1588</id>
    <activation>
        <activeByDefault>true</activeByDefault>
    </activation>
    <properties>
        <argLine>-Djdk.net.URLClassPath.disableClassPathURLCheck=true</argLine>
    </properties>
</profile>
```

* * *
Creation date: _2018-11-11_

[HSCQ5MSCNFFCN1L1]: https://stackoverflow.com/questions/53010200/maven-surefire-could-not-find-forkedbooter-class?noredirect=1&lq=1
[HBDO9]: http://bugs.debian.org/911925
[HIAOJBS1F1PCAJPSI3TC1]: https://issues.apache.org/jira/browse/SUREFIRE-1588?focusedCommentId=16671777&page=com.atlassian.jira.plugin.system.issuetabpanels%3Acomment-tabpanel#comment-16671777
[HSCA51]: https://stackoverflow.com/a/53016532/161312