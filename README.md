IA
=========

Provisionar a infra estrutura com deploy simples de pagina web "HelloWorld"
Executar o playbook ansible.


Dependências
------------
```
Ansible 2.x
Terraform 13.x
```

Variáveis
--------------

```
pacotes_instalados:
  - httpd
  - httpd-devel
  - mod_ssl

portas_abertas:
  - { porta: 80, protocolo: tcp }


httpd_path: "/etc/httpd"
httpd_conf_path: "{{ httpd_path }}/conf.d"
httpd_port_file: "{{ httpd_path }}/conf/httpd.conf"
httpd_vhost_path: "{{ httpd_path }}/conf.d"
httpd_service: "httpd"
httpd_user: "apache"
httpd_group: "apache"
ssl_certs_path: "/etc/httpd/conf.d/ssl/SiteBlindado"

httpd_listen_ip: "*"
httpd_listen_port: 80
httpd_listen_port_ssl: 443

httpd_ignore_missing_ssl_certificate: true

httpd_ssl_protocol: "All -SSLv2 -SSLv3"
httpd_ssl_cipher_suite: "AES256+EECDH:AES256+EDH"

# Set initial apache state. Recommended values: `started` or `stopped`
httpd_state: started

```

License
-------

MIT

Author Information
------------------

Denys Ladislau

denys.atyla@gmail.com

