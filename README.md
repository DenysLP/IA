IA
=========

Provisionar a infra estrutura com deploy simples de pagina web "HelloWorld"

1. Set o token da Digital ocean 

```
export DO_API_TOKEN=XXXXXXXXXXXXXXX
```

2. Execute o playbook droplet.yml para criar o Droplet na Digital Ocean
```
ansible-playbook -i hosts droplet.yml
```

Saida do Playbook deverá ser algo como 

```
PLAY [localhost] *****************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************************************************************************************************
ok: [localhost]

TASK [ia.terraform : Criando o droplet] ******************************************************************************************************************************************************************************************
changed: [localhost]

TASK [ia.terraform : Informação do droplet] **************************************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": "IP Address é: 67.205.149.107"
}

TASK [ia.terraform : Set uma variavel fact para registrar a variavel droplet_ip] *************************************************************************************************************************************************
ok: [localhost]

TASK [ia.terraform : Adicionando o novo host ao Ansible inventory] ***************************************************************************************************************************************************************
changed: [localhost]

TASK [ia.terraform : Aguardando o servidor responder SSH] ************************************************************************************************************************************************************************
ok: [localhost]

PLAY RECAP ***********************************************************************************************************************************************************************************************************************
localhost                  : ok=6    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

```

![](/image1.PNG)

3. Execute o playbook playbook.yml para provisionar o ambiente (Jenkins, Gitlab).

```
ansible-playbook -i hosts playbook.yml
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
DO_API_TOKEN: "XXXXXXXXXXXXXXX"


```

License
-------

MIT

Author Information
------------------

Denys Ladislau

denys.atyla@gmail.com

