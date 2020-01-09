This a simplified version (no symfony) of : https://dev.to/_mertsimsek/using-xdebug-with-docker-2k8o

In THIS alchemy project, note (in DockerFile) : 
- xdebug.remote_port=9051
- xdebug.idekey=mertblog.net
- xdebug.remote_host=docker.for.mac.localhost

So The xdebug port in phpstorm must be set to 9051.

More important : the "docker.for.mac.localhost" might work only on macos, read about that in mertblog.

nb : there is a pb in nginx conf (nginx/app.conf) to be fixed :

In the browser, DON'T call index.php, but instead call a NONEXISTING php file. This will fallback to index.php : 

http://localhost:8888/foo.php?XDEBUG_SESSION_START=mertblog.net

This is because the nginx conf was copy/paste from the "mertsimek" example, which was supposed to run a symfony app, not a single php file.

Anyway, in this poc project (on mac...), breakpoints are functionnal in phpstorm.

