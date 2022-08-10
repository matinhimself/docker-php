# docker-php
## usage
- cd to `cd .docker/php-cli/ssh/`
- delete already existing pubkey file `rm id_rsa.pub`
- generate new keypair using your keygen or just paste your own pubkey (`ssh-keygen -t rsa -b 4096 -f id_rsa.pub`)
- in project root build project using `make rebuild` then run them using `make run`
- open bash shell in container using `make bash` and find and save php interpreter path using `whereis php`
- get and save php extensions folder with `php-config --extension-dir` 
- add a new php cli interpreter in your php-storm settings
- select ssh and use your generated id_rsa.pub`s ssh config as keypair and container php interpreter path u found before
- php-storm should now detect interpreter and xdebug debugger hooked with its configuration file
- add the php extension folder following with `xdebug.so` as `Debugger extesion`. (i.e ‍`/usr/local/lib/php/extensions/no-debug-non-zts-20210902/xdebug.so`)
- set `-dxdebug.client_host=host.docker.internal` as Configuration option, somehow php-storm override xdebug config itself so we should pass it as debug option too



