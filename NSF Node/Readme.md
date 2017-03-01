On the NSF side, 

Snort IDS is installed and configured in the VM. Snort is an open source IDS widely used as a Network Intrusion Detection System (NIDS) and can be downloaded from www.snort.org
Snort Installation can be followed as described in https://www.unixmen.com/install-snort-nids-ubuntu-15-04/

Once Snort is installed and configured it can be always tested using 

 `` # snort -T -c /etc/snort/snort.conf ``

**Code**
In the Code folder,
Entire code is written in java using Eclipse IDE, hence the file paths mentioned in the respective programs will be according to Eclipse’s workspace file structure.

**Client.java**
This file contains the code to accept incoming connection from the Controller. Once the NSF receives the XML file from Controller, it reads the contents and prints to the user.

**TranslateXML2IDSRule.java **
This program translates the XML file and extracts necessary pieces of information (as shown in the figure below) required to construct Snort rule. Due to the limited information provided by the consumer of I2NSF framework, more importance is given in constructing Snort rule header and some mandatory rule options like “msg”, “sid”.  The figures below give more detailed view of Snort rule header with an example.
 

Eg:
 
**WriteInRules.java**
This program writes the translated rule into exact Snort rules file which contains all the rules executed by Snort.
Once the rule is inserted into the Snort rules file, Snort is re-executed to make sure Snort is running successfully with the new rule inserted.
