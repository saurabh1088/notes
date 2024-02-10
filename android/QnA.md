# Android QnA

## Can two apps in Android share data? If yes then how?
*This approach listed below however is deprecated from API level 29.*
Two apps can share smae Linux user ID, and then they are able to access each other's files. Apps sharing same linux user ID
will:
1. Be able to access each other'f file
2. Run within same process
3. Share the same virtual memory(VM) in which apps run
Apps sharing Linux user ID should be signed with same certificate.

In Android manifest xml file one can have set *android:sharedUserId* same for two or more apps to have them work in shared
environment. However this *android:sharedUserId* is deprecated from API level 29.
