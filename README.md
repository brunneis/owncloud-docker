# ownCloud X Docker image
Docker image of ownCloud Server 10 (Community) on PHP 7.0.

## Start ownCloud
Starting the ownCloud X instance listening on port 80 is as easy as the following:

`$ docker run -d -p 80:80 brunneis/owncloud-10`
Then go to [http://localhost/](http://localhost/) and go through the wizard. By default this container uses SQLite for data storage, but the wizard should allow for connecting to an existing database.

## Persistent data
All data beyond what lives in the database (file uploads, etc) is stored within the default volume `/var/www/html`. With this volume, ownCloud will only be updated when the file `version.php` is not present.

- `-v /<mydatalocation>:/var/www/html`
For fine grained data persistence, you can use 3 volumes, as shown below.

- `-v /<mydatalocation>/apps:/var/www/html/apps` installed / modified apps
- `-v /<mydatalocation>/config:/var/www/html/config` local configuration
- `-v /<mydatalocation>/data:/var/www/html/data` the actual data of your ownCloud
