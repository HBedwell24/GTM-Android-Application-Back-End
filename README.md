# GTM Android Application Back End
The PHP files fundamental to ensuring that data is successfully transmitted to and from a remote MySQL database in order to promote a satisfactory login experience.

## 1. Running the Application Locally
In order to run the application successfully from a user's desktop, one will need to have posession of an Apache distribution such as XAMPP or WAMP, which allows for a local web server to be ran on the host computer's localhost domain. A safe way to download these software bundles can be found as follows:

[Download XAMPP from SourceForge](https://sourceforge.net/projects/xampp/)

**OR**

[Download WAMP from SourceForge](https://sourceforge.net/projects/wampserver/)

The installation wizard will guide you through setting the software up on your local device, and should be a relatively trivial task.

### 1.1 Starting Up XAMPP/WAMP
Once the installation setup has concluded, one can access XAMPP/WAMP by finding it through the search bar feature specific to the OS at hand, or by simply locating the application file within your machine's File Explorer. Depending on the Apache distribution you have chosen to download, clicking the icon of the application will have varying results. In the case you have chosen XAMPP, one would simply have to click the application, to which the user would be greeted with a list of modules in a popup window (with Apache and MySQL being the primary areas of concern). On the contrary, WAMP is handled more so like an executable, and needs to be granted permission each time it is opened. Allowing it to make changes to the computer will add a red icon to the lower taskbar, signifying that WAMP's inline services are offline, and that one needs to start them by pressing 'Start All Services'.

Be sure to start either distribution's respective services as mentioned above, and then proceed to open up a window in the Internet browser of your choice. Type in 'localhost/phpmyadmin' in the address bar, and then log in if applicable (with root as your username, and a blank string as your password, provided that you have not changed the default password). If done correctly, you will now have access to the PHPMyAdmin dashboard, which is what will be used in the next steps to create the much needed database tables.

However, to go about this, one will first have to create a database to hold the tables. To do this, click 'New' in the top part of the left-most navigation menu, and then proceed to enter in a name that you would prefer for the database to be referenced by within the PHP codebase. Keep all other settings as default, and then press 'Create'.

### 1.2 Creating the Database Tables
What will follow is a blank screen informing the user that there are no existent tables within the database. To add the two tables, proceed to the 'SQL' located tab located above the prior mentioned alert, and then enter the following queries:

#### Password Reset Request
```sql
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET AUTOCOMMIT = 0;
START TRANSACTION;
SET time_zone = "+00:00";

CREATE TABLE `password_reset_request` (
  `sno` int(11) NOT NULL,
  `email` varchar(50) NOT NULL,
  `encrypted_temp_password` varchar(256) NOT NULL,
  `salt` varchar(10) NOT NULL,
  `created_at` datetime DEFAULT NULL
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

ALTER TABLE `password_reset_request`
  ADD PRIMARY KEY (`sno`);

ALTER TABLE `password_reset_request`
  MODIFY `sno` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;
COMMIT;
```

#### Users
```sql
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET AUTOCOMMIT = 0;
START TRANSACTION;
SET time_zone = "+00:00";

CREATE TABLE `users` (
  `sno` int(11) NOT NULL,
  `unique_id` varchar(23) NOT NULL,
  `name` varchar(50) NOT NULL,
  `email` varchar(50) NOT NULL,
  `encrypted_password` varchar(256) NOT NULL,
  `salt` varchar(10) NOT NULL,
  `created_at` datetime DEFAULT NULL
) ENGINE=MyISAM DEFAULT CHARSET=latin1;

ALTER TABLE `users`
  ADD PRIMARY KEY (`sno`);

ALTER TABLE `users`
  MODIFY `sno` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=33;
COMMIT;
```

Doing so will result in two data schemas, which will act as a baseline for verifying and receiving user data sent to and from the Android forms, as well as act as a means for facilitating inbound password reset requests.

### 1.3 Downloading the Repository
Lastly, you will be required to download and unzip the file contents of this repository and place them on the Apache web server to be served on your local domain. To do so, click on the "Clone or Download" dropdown at the top right of the repository dashboard and then click "Download ZIP". Navigate to the location of your XAMPP/WAMP installation on your local machine and you will find a htdocs/www folder. Within the htdocs/www folder, create a sub-folder named after the database created previously. This sub-folder will be where you extract the contents of the ZIP folder so that they may be accessed accordingly.

