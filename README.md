# apache-userdir-php
Ferramentas e modelo de administração de apache com mod_userdir e php-fpm

## setup
No nginx:
1. criar usuário vhost com chave de SSH
2. adicioná-lo no `/etc/sudoers.d` como em [etc/vhost](etc/vhost)
3. criar link para o `ime-gen-vhost` em `/usr/local/bin/ime-gen-vhost` (ou algo que case com o sudoers)

No apache:
1. criar diretório `/etc/apache2/php-enabled`
2. adicionar o [etc/userphp.conf](etc/userphp.conf) em `/etc/apache2/conf-enabled` e habilitá-lo
