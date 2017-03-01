Controller Node:Contains the code for the GUI taken from https://github.com/kimjinyong/i2nsf-framework/

Requirements to setup GUI
•	MySQL
You can install and configure following the steps in this link
https://www.youtube.com/watch?v=uqaoGTnxqNw&t=93s
There are some frequent issues encountered while installing MySQL on Ubuntu. Some of these links can be useful to resolve these,
https://ubuntuforums.org/showthread.php?t=1836919
https://www.digitalocean.com/community/tutorials/how-to-use-open-monitoring-distribution-with-check_mk-on-ubuntu-14-04
If you are new or not proficient in using MySQL, some of the frequently used commands are listed in https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial

•	Apache Web Server
You can install and configure following the steps in this link https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04
In the above page at the command: $sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql
Use command: $sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt php5-mysql
Use (when needed): $ sudo /etc/init.d/apache2 restart
•	PYANG
This is an open source YANG validation tool and can be installed following these steps,
$sudo apt-get install python-setuptools
$git clone https://github.com/mbj4668/pyang
$cd pyang
$sudo python setup.py install

If you are new to PYANG, more information can be found at https://github.com/mbj4668/pyang/wiki/Tutorial
PYANG is useful in this project primarily for validating XML, building UML diagrams from YANG model. But this procedure for validating XML and building UML diagrams is automated in my code (ExecComnd.java).

Code
In the Code folder,
Entire code is written in java using Eclipse IDE, hence the file paths mentioned in the respective programs will be according to Eclipse’s workspace file structure.

YangTranslate.java
This program translates the input high level XML file and replaces it with precise information.
Eg: “HostA” to “10.10.10.10” (its corresponding IP address)

ExecComnd.java
Once the XML file is translated using the above program, it is validated using PYANG.
This program will give you with a list of options that you can perform using PYANG and selecting an option will produce the result as the commands are automated in this file.

MySQLConnection.java
This program extracts the necessary information from the XML file and inserts and saves in the database for other functionalities of I2NSF framework like,
•	Retrieving the current rules present in the database
•	Checking if there are any duplicate or redundant policy requests
•	Consumer of I2NSF requesting a specific information on a policy etc

Connection.java
Once the XML is validated with PYANG this file is sent over to the NSF by establishing a secure communication by this program.
