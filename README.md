# apache-userdir-php
Ferramentas e modelo de administração de apache com mod_userdir e php-fpm.

A ideia é subir, atrás de um nginx de entrada, um apache2 com php-fpm que seja habilitado por usuário. Essencialmente criaremos um pool do tipo _ondemand_ por usuário e o referenciaremos a partir de um arquivo de configuração do apache. Isso permite que cada usuário tenha seu conjunto de processos que rodam PHP sem comprometer o servidor todo como no caso de um CGI ou mesmo do mod-php. Os scripts automatizam esse processo.

## setup
No nginx:
1. criar usuário vhost com chave de SSH
2. adicioná-lo no `/etc/sudoers.d` como em [etc/vhost](etc/vhost)
3. criar link para o `ime-gen-vhost` em `/usr/local/bin/ime-gen-vhost` (ou algo que case com o sudoers)

No apache:
1. criar diretório `/etc/apache2/php-enabled`
2. adicionar o [etc/userphp.conf](etc/userphp.conf) em `/etc/apache2/conf-enabled` e habilitá-lo

## como usar
Para ativar o PHP, logar no **apache** e rodar:

`./ime-enable-php username`, onde `username` é o nome do usuário.

Exemplo:
```bash
./ime-enable-php rickastley
```

Para criar o virtual host:
1. criar a entrada de DNS
2. logar no **apache** e rodar `./ime-gen-vhost domínio_não_fqdn`

Exemplo:
```bash
# se o domínio for rickastley.ime.usp.br
./ime-gen-vhost rickastley
```
