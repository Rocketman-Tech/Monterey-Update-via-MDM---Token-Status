**About**

In order to update macOS Monterey 12.0.1 or later via an MDM utilizing Apples newly introduced 'InstallLater' MDM Command, a bootstrap token must be escrowed to the MDM Server.

To determine the Escrow status of a Bootstrap Token I've included 3 Extension Attributes. 

*Bootstrap.xml*
- Determines the escrowed status of the Bootstrap Token


*Secure Token users.xml*
- Determines SecureToken enabled User(s)
- Displays SecureToken enabled Username(s)
- User(s) can escrow the Bootstrap Token


*Secure Token users w_Unknown.xml*
- Determines SecureToken enabled User(s)
- Displays "Unknown Secure Token Holders" if Unknown
- Displays SecureToken enabled Username(s) if Known
_____________________________________________________________________________________________________

**How to use**

Download the 3 .xml files from this repo & Navigate to your Jamf Pro Server, path to upload is below.

All Settings -> Computer Management (Management Framework) -> Extension Attributes -> Upload

*Recommended Workflow*
- macOS 12.0.1+ 
- Enrolled via ADE using Prestage Enrollment via Jamf Pro
- Filevault Configuration Profile pushed during enrollment & enabled at First Login
- End User Graphically Logs in
- SecureToken is granted & Bootstrap token is escrowed.

If older version of macOS - Upgrade to macOS Monterey 12.0.1+ & then you can upgrade with MDM Deferal Command.

_____________________________________________________________________________________________________

**How to Obtain a SecureToken in order to escrow the Bootstrap Token?**

Requirements: Automated Device Enrollment (Formerly DEP) & MDM (Jamf)

macOS Catalina (10.15.4+)
- An account created by an end user during setup assistant automatically gets a SecureToken. 
- If you skip account creation, the next local Admin that authenticates receives a SecureToken.
- Enabling FileVault on a SecureToken-less system provides the account enabling FileVault a SecureToken. (Mobile or Local) 
- Local Standard Accounts created outside of Setup Assistant via 3rd Party app do not receive a SecureToken. (NoMad, Jamf Connect, etc)

macOS Big Sur (11.0.1+)
- Local Standard Accounts created outside of the setup assistant do get a SecureToken. 

_____________________________________________________________________________________________________


**Good Reads**

https://docs.jamf.com/technical-articles/Manually_Leveraging_Apples_Bootstrap_Token_Functionality.html
https://support.apple.com/guide/deployment/use-secure-and-bootstrap-tokens-dep24dbdcf9e/web
