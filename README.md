# Dockerized Magento 2 #


## Justification ##

The main idea of the present is to have a way to quickly setup a magento 2 
developing environment.
This will build 3 containers:
* The Application Container: Containing PHP, Apache and volumes so that 
we can have the application's code accesible from our filesystem
* The database Container: Containing the database with a volume mapped to our
filesystem so that we maintain the data's persistency.
* A PHPMyAdmin Container: Just in case we don't have a database editor 
installed (It's also very useful for a productive environment).

## Usage ##

1. Clone the project and cd on it.
2. Build the containers with: "docker-compose up --build -d"
3. Delete the "index.php" file inside the app folder (That's just a friendly
reminder for those who jump the gun! ;)) and copy your magento files there.
4. Finally, go to http://localhost your browser (Or http://localhost/setup if
you actually do not have magento installed with those files).
5. Enjoy!

