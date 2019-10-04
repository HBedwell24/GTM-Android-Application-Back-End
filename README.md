# GTM Android Application Back End
The PHP files fundamental to ensuring that data was successfully transmitted to and from a remote MySQL database in order to promote a satisfactory login experience.

## Running the Application Locally
In order to run the application successfully from a user's desktop, one will need to have posession of an Apache distribution such as XAMPP or WAMP, which allows for a local web server to be ran on the host computer's localhost domain. A safe way to download these software bundles can be found as follows:

XAMPP: https://sourceforge.net/projects/xampp/

WAMP: https://sourceforge.net/projects/wampserver/

The installation wizard will guide you through setting the software up on your local device, and should be a relatively trivial task.

### Starting Up XAMPP
Once the installation setup has concluded, one can access XAMPP by finding it through the search bar feature specific to the OS at hand, or by simply locating the application file within the machine's File Explorer. Clicking the icon of the application will bring up a list of modules, with Apache and MySQL being the primary areas of concern. 

Be sure to start both of these services, and then proceed to open up a window in the Internet browser of your choice. Type in 'localhost/phpmyadmin' in the address bar, and then log in if applicable (with root as your username, and a blank string as your password). If done correctly, you will now have access to the PHPMyAdmin dashboard, which is what will be used in the next steps to create the much needed database tables.

However, to go about this, one will first have to create a database to hold the tables. To do this, click 'New' in the top part of the left-most navigation menu, and then proceed to enter in a name that you would prefer for the database to be referenced by within the PHP codebase. Keep all other settings as default, and then press 'Create'.

### Creating the Database Tables
