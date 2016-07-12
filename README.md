macOS LAPS (Local Administrator Password Solution)
==================================================

This Python script will use the macOS dscl utility to determine if the
local administrator password has expired as specified by the Active Directory
attribute dsAttrTypeNative:ms-Mcs-AdmPwdExpirationTime. If this is the case
then a new randomly generated password will be set for the local admin account
and a new expiration date will be set. The LAPS password is stored in the
Active Directory attribute dsAttrTypeNative:ms-Mcs-AdmPwd.

Requirements
------------

Since we are utilizing the dscl utility you will only need to set your
parameters. These parameters are stored in /Libary/Preferences/edu.psu.macoslaps.plist
or if you are using an MDM you can use Custom Settings. The following parameters
must be set or the application will use the defaults:

**LocalAdminAccount** - Local Administrator Account. Default is 'admin'  
**DaysTillExpiration** - Expiration date of random password. Default is 60 Days  
**PasswordLength** - Length of randomly generated password. Default is 8  

Installation Instructions
-------------------------
At this time you can clone the repo or download a zip of the repo and then put
the script in /usr/local. Then place the LaunchDaemon in /Library/Launch Daemons.
This will run at 3 times a day between 8 A.M. and 5 P.M.

Logging
-------
The script will also perform logging so that you know when the password is changed
and its new expiration date or when the current unchanged password will expire. This
file is stored in /Library/Logs/ as macOSLAPS.log

Feedback
--------
I have only so far tested this in my environment so I would love for other people
to test this and determine if it also fits their environment.

Special Thanks
--------------
A very special thanks to @rustymyers as he was very helpful in determinining how AD
stores the Time.
