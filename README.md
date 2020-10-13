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

![](/images/image1.PNG)


3. Execute o playbook playbook.yml para provisionar o ambiente (Docker, Jenkins, Gitlab).

```
ansible-playbook -i hosts playbook.yml

ansible-playbook -i hosts playbook.yml --check

PLAY [docker] *******************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************************************************************************************************
ok: [104.248.117.239]

TASK [ia.docker : Install Docker] ***********************************************************************************************************************************************************************************************************
ok: [104.248.117.239] => (item=[u'apt-transport-https', u'ca-certificates', u'curl', u'software-properties-common'])

TASK [ia.docker : Adcionando GPG Key] *******************************************************************************************************************************************************************************************************
ok: [104.248.117.239]

TASK [ia.docker : Set repositorio] **********************************************************************************************************************************************************************************************************
ok: [104.248.117.239]

TASK [ia.docker : Update pacotes] ***********************************************************************************************************************************************************************************************************
changed: [104.248.117.239]

TASK [ia.docker : Install Docker] ***********************************************************************************************************************************************************************************************************
ok: [104.248.117.239]

TASK [ia.docker : Install docker-compose] ***************************************************************************************************************************************************************************************************
ok: [104.248.117.239]

TASK [ia.ambiente : Copiando docker-compose.yml] ********************************************************************************************************************************************************************************************
changed: [104.248.117.239]

TASK [ia.ambiente : Exeutando docker-compose.yml] *******************************************************************************************************************************************************************************************
skipping: [104.248.117.239]

PLAY RECAP **********************************************************************************************************************************************************************************************************************************
104.248.117.239            : ok=8    changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

```

4. Após o Ambiente Criado Faça a integração CI/CD do Gitlab/Jenkins do projeto Hello World com a Job Hello World

4.1 Crie o token do Gitlab

![](/images/image2.PNG)


4.2 Crie/Configure plugins, Job, credenciais, e integração no Jenkins (Obs: Pode ser automatizada também quando se tem um job template no Jenkins)

![](/images/image3.PNG)

![](/images/image4.PNG)

![](/images/image5.PNG)

![](/images/image6.PNG)

![](/images/image7.PNG)


5. Após toda configuração e integração, todo push realizado no projeto Automaticamente aplica a mudança no ambiente:

![](/images/image8.PNG)

![](/images/image9.PNG)

![](/images/image10.PNG)

![](/images/image11.PNG)


6. Monitoramento (Obs: Devido ao tempo e por esta um pouco corrido utilizei o codigo https://github.com/stefanprodan/dockprom) 

![](/images/image12.PNG)

![](/images/image13.PNG)

![](/images/image14.PNG)

![](/images/image15.PNG)


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

