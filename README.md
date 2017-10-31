# Commands-and-Code
Useful commands

Reset a MySQL root password
Last updated on: 2016-06-13 Authored by: Rackspace Support
The MySQL root password allows the root user to have full access to the MySQL database. You must have (Linux) root or (Windows) Administrator access to the Cloud Server to reset the MySQL root password.

Note: The Cloud Server (Linux) root or (Windows) Administrator account password is not the same as the MySQL password. The Cloud Server password allows access to the server. The MySQL root password allows access only to the MySQL database.

Use the following steps to reset a MySQL root password by using the command line interface.

      Stop the MySQL service

(Ubuntu and Debian) Run the following command:

      sudo /etc/init.d/mysql stop
(CentOS, Fedora, and Red Hat Enterprise Linux) Run the following command:

      sudo /etc/init.d/mysqld stop

Start MySQL without a password

Run the following command. The ampersand (&) at the end of the command is required.

      sudo mysqld_safe --skip-grant-tables &
Connect to MySQL

Run the following command:

      mysql -uroot
Set a new MySQL root password

Run the following command:

use mysql;

      update user set password=PASSWORD("mynewpassword") where User='root';
      flush privileges;
      quit
      Stop and start the MySQL service

(Ubuntu and Debian) Run the following commands:

      sudo /etc/init.d/mysql stop
      ...
      sudo /etc/init.d/mysql start
(CentOS, Fedora, and Red Hat Enterprise Linux) Run the following commands:

      sudo /etc/init.d/mysqld stop
      ...
      sudo /etc/init.d/mysqld start
Log in to the database

Test the new password by logging in to the database.
      
      mysql -u root -p
      
Generate Key pair:

      ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

The keys will be saves in .ssh folder within the user folder.
Add the SSH key to the agent:
      
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.

Start the ssh-agent in the background.

      eval "$(ssh-agent -s)"
      Agent pid 59566
If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

      Host *
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_rsa
      
Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

      $ ssh-add -K ~/.ssh/id_rsa
