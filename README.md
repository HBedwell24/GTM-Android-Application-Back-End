# GTM Android Application Back End
The PHP files fundamental to ensuring that data is successfully transmitted to and from a remote MySQL database in order to promote a satisfactory login experience.

## 1. Running the Application Locally
In order to run the application successfully from a user's desktop, one will need to have posession of an Apache distribution such as XAMPP or WAMP, which allows for a local web server to be ran on the host computer's localhost domain. A safe way to download these software bundles can be found as follows:

[Download XAMPP from SourceForge](https://sourceforge.net/projects/xampp/)

[Download WAMP from SourceForge](https://sourceforge.net/projects/wampserver/)

The installation wizard will guide you through setting the software up on your local device, and should be a relatively trivial task.

### 1.1 Starting Up XAMPP
Once the installation setup has concluded, one can access XAMPP by finding it through the search bar feature specific to the OS at hand, or by simply locating the application file within the machine's File Explorer. Clicking the icon of the application will bring up a list of modules, with Apache and MySQL being the primary areas of concern. 

Be sure to start both of these services, and then proceed to open up a window in the Internet browser of your choice. Type in 'localhost/phpmyadmin' in the address bar, and then log in if applicable (with root as your username, and a blank string as your password). If done correctly, you will now have access to the PHPMyAdmin dashboard, which is what will be used in the next steps to create the much needed database tables.

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

Doing so will result in two tables, which will act as a baseline for verifying and receiving user data sent to and from the Android forms, as well as act as a means for facilitating inbound password reset requests.

