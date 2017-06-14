macOS LAPS (Local Administrator Password Solution)
==================================================
Python script that utilizes Open Directory to determine if the
local administrator password has expired as specified by the Active Directory
attribute dsAttrTypeNative:ms-Mcs-AdmPwdExpirationTime. If this is the case
then a new randomly generated password will be set for the local admin account
and a new expiration date will be set. The LAPS password is stored in the
Active Directory attribute dsAttrTypeNative:ms-Mcs-AdmPwd. This attribute can
only be read by those designated to view the attribute. The computer record
can write to this attribute but it cannot read.

Requirements
------------

The following parameters must be set or the application will use the defaults:

**LocalAdminAccount** - Local Administrator Account. Default is 'admin'  
**DaysTillExpiration** - Expiration date of random password. Default is 60 Days  
**PasswordLength** - Length of randomly generated password. Default is 12  
**RemoveKeyChain** - Remove the local admin keychains after password change. (Recommended)  
**RemovePassChars** - Exclude any characters you'd like from the randomly generated password (In String format)  

These parameters are set in the location /Libary/Preferences/edu.psu.macoslaps.plist
or you can use your MDM's Custom Settings to set these values.

Exclusions
----------------
As pointed out by one of my fellow colleagues, the **'** key on macOS cannot be used on Windows without opening
the character map to enter it. Since this is very detriment to using a LAPS password from a Windows client I have made this key excluded by default.

Installation Instructions
-------------------------
At this time you can clone the repo or download a zip of the repo or you can
use the package created using Packages to install. This script will run
3 times a day between 8 A.M. and 5 P.M. at 9 A.M., 1 P.M. and 4 P.M.

Logging
-------
The script will also perform logging so that you know when the password is changed
and its new expiration date or when the current unchanged password will expire. This
file is stored in /Library/Logs/ as macOSLAPS.log

Feedback
--------
All feedback I have received is positive so far but please continue testing this in your environment and let me know the results.

Local Admin Keychain
--------
By default, the local admin you choose has its keychain deleted since we wouldn't know the randomized password.

Credits
--------------
* Rusty Myers - For helping to determine that Windows has its own time method vs
Epoch time
* Michael Lynn - For critiquing and assisting with generating the random password
* Ben Toms - For sharing code from ADPassMon to query Active Directory with Open
Directory
* Tom Burgin - For showing me the benefits and how to use Open Directory with Python
* Per Olofsson - For also assisting with Open Directory commands
* Clayton Burlison - For keeping my lack of markdown skills in check
