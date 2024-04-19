## Commands
Extract all Subnet and Sites from AD using TrustedSec's BOF "ldapsearch" :
```
ldapsearch (cn=*) cn,description 0 domain.local "CN=Subnets,CN=Sites,CN=Configuration,dc=domain,dc=local"
```
Search for all Pre-Created Computer accounts from AD using TrustedSec's BOF "ldapsearch" :  
Source : https://www.trustedsec.com/blog/diving-into-pre-created-computer-accounts/?utm_campaign=Targeted%20Operations
```
ldapsearch (&(userAccountControl=4128)(logonCount=0)) samaccountname 0 domain.local ""
```
Search for all enabled Windows Server 2008 that their lastlogon is >= to '2024-02-02 07:37' (133513510232969784):
```
ldapsearch "(&(&(&(&(samAccountType=805306369)(!(primaryGroupId=516)))(objectCategory=computer)(operatingSystem=Windows Server 2008*)(!userAccountControl:1.2.840.113556.1.4.803:=2)(lastlogon>=133513510232969784))))" sAMAccountName,lastlogon
```
Extracts ASR Rules - See (https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference?view=o365-worldwide#asr-rule-to-guid-matrix)
```
reg_query HKLM "SOFTWARE\Policies\Microsoft\Windows Defender\Windows Defender Exploit Guard\ASR\Rules"
```
## Useful links
OPSec:
```
https://blog.cobaltstrike.com/2017/06/23/opsec-considerations-for-beacon-commands/
https://www.cobaltstrike.com/help-sleep-mask-kit
```
SANS DFIR Normal Parent process tree examples:
```
https://sansorg.egnyte.com/dl/ZkAyckjFTI
```
Agressor Script functions (CNA):
```
https://www.cobaltstrike.com/aggressor-script/functions.html
```
Agressor Scripts:
```
https://github.com/harleyQu1nn/AggressorScripts
https://github.com/harleyQu1nn/AggressorScripts/blob/master/ProcessColor.cna
```
BOF:
```
https://github.com/trustedsec/CS-Situational-Awareness-BOF
https://github.com/ajpc500/BOFs
https://cobalt-strike.github.io/community_kit/
```
User-Defined Reflective Loader:
```
https://github.com/mgeeky/ElusiveMice
https://github.com/boku7/CobaltStrikeReflectiveLoader
https://www.cobaltstrike.com/help-user-defined-reflective-loader
```
Windows Error codes:
```
https://docs.microsoft.com/en-us/windows/win32/debug/system-error-codes--0-499-
```
Mr-Un1k0d3r:
```
https://github.com/Mr-Un1k0d3r/ADHuntTool
https://github.com/Mr-Un1k0d3r/EDRs
https://github.com/Mr-Un1k0d3r/RedTeamCCode
https://github.com/Mr-Un1k0d3r/RedTeamCSharpScripts
```
SharpCollection:
```
https://github.com/Flangvik/SharpCollection
```
Universal UnHook (now flagged by the latest versions of some EDRs: kind of tamper protection):
```
https://github.com/rsmudge/unhook-bof
```
Inline Execute-Assembly:
```
https://github.com/anthemtotheego/InlineExecute-Assembly
```
