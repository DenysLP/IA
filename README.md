IA
=========

Provisionar a infra estrutura com deploy simples de pagina web "HelloWorld"

1. Execute o comando terraform plan posteriormente o apply caso não ocorra erro.

```
[root@template IA]# terraform plan
var.do_token
  Enter a value: "XXXXXXXXXXXXXXXXXXXXXXXXXXXXX"

Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.


------------------------------------------------------------------------

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # digitalocean_droplet.do_droplet will be created
  + resource "digitalocean_droplet" "do_droplet" {
      + backups              = false
      + created_at           = (known after apply)
      + disk                 = (known after apply)
      + id                   = (known after apply)
      + image                = "ubuntu-16-04-x64"
      + ipv4_address         = (known after apply)
      + ipv4_address_private = (known after apply)
      + ipv6                 = false
      + ipv6_address         = (known after apply)
      + ipv6_address_private = (known after apply)
      + locked               = (known after apply)
      + memory               = (known after apply)
      + monitoring           = false
      + name                 = "testing-ia"
      + price_hourly         = (known after apply)
      + price_monthly        = (known after apply)
      + private_networking   = false
      + region               = "fra1"
      + resize_disk          = true
      + size                 = "s-1vcpu-1gb"
      + status               = (known after apply)
      + tags                 = [
          + "ia-testing",
        ]
      + urn                  = (known after apply)
      + vcpus                = (known after apply)
      + volume_ids           = (known after apply)
    }

Plan: 1 to add, 0 to change, 0 to destroy.
```

Logo após crie o Droplet
```
[root@template IA]# terraform apply
var.do_token
  Enter a value: "XXXXXXXXXXXXXXXXXXXXXXXXXXXXX"


An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # digitalocean_droplet.do_droplet will be created
  + resource "digitalocean_droplet" "do_droplet" {
      + backups              = false
      + created_at           = (known after apply)
      + disk                 = (known after apply)
      + id                   = (known after apply)
      + image                = "ubuntu-16-04-x64"
      + ipv4_address         = (known after apply)
      + ipv4_address_private = (known after apply)
      + ipv6                 = false
      + ipv6_address         = (known after apply)
      + ipv6_address_private = (known after apply)
      + locked               = (known after apply)
      + memory               = (known after apply)
      + monitoring           = false
      + name                 = "testing-ia"
      + price_hourly         = (known after apply)
      + price_monthly        = (known after apply)
      + private_networking   = false
      + region               = "fra1"
      + resize_disk          = true
      + size                 = "s-1vcpu-1gb"
      + status               = (known after apply)
      + tags                 = [
          + "ia-testing",
        ]
      + urn                  = (known after apply)
      + vcpus                = (known after apply)
      + volume_ids           = (known after apply)
    }

Plan: 1 to add, 0 to change, 0 to destroy.


Warning: Interpolation-only expressions are deprecated

  on provider.tf line 4, in provider "digitalocean":
   4:     token   = "${var.do_token}"

Terraform 0.11 and earlier required all non-constant expressions to be
provided via interpolation syntax, but this pattern is now deprecated. To
silence this warning, remove the "${ sequence from the start and the }"
sequence from the end of this expression, leaving just the inner expression.

Template interpolation syntax is still used to construct strings from
expressions when the template includes multiple interpolation sequences or a
mixture of literal strings and interpolations. This deprecation applies only
to templates that consist entirely of a single interpolation sequence.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

digitalocean_droplet.do_droplet: Creating...
digitalocean_droplet.do_droplet: Still creating... [10s elapsed]
digitalocean_droplet.do_droplet: Still creating... [20s elapsed]
digitalocean_droplet.do_droplet: Still creating... [30s elapsed]
digitalocean_droplet.do_droplet: Still creating... [40s elapsed]
digitalocean_droplet.do_droplet: Still creating... [50s elapsed]
digitalocean_droplet.do_droplet: Creation complete after 1m0s [id=211834365]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

```


Dependências
------------
```
Criar um conta na Digital Ocean
Criar um Token na Digital Ocean 
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

