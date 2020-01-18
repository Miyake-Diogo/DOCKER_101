# Tutorial Docker - Curso Linuxtips

Boa parte do material me bassei no curso descomplicando o docker do Jefersson da LinuxTips.  

[Curso Descomplicando o Docker - 2016](https://www.youtube.com/playlist?list=PLf-O3X2-mxDkiUH0r_BadgtELJ_qyrFJ_)  

Comandos utilizados em ambiente Linux!!

## Instalando o Docker
Para instalar o Docker digite o comando CURL na linha de comando:  
```
sudo curl -fsSL https://get.docker.com/ | sh
```
Caso já tenha o docker instalado ele fará o update da versão. Qualquer dúvida veja a [documentação](https://docs.docker.com/)
Para verificar a instalação:  
```
sudo docker --version
```
Caso ocorra algum erro verifique se o serviço esta desativado, para isso rode im dos comandos abaixo:  
```
/etc/init.d/docker start
```
ou
```
sudo service docker start
```
### Comandos docker sem sudo
Para utilizar o docker sem sudo tem duas opções:
1. Adicionar seu usuário a lista de usuarido do docker - Fonte: [Blog Alura](https://cursos.alura.com.br/forum/topico-quase-todos-comandos-docker-so-funcionam-com-sudo-22028)
2. Acessar como usuário root - Use o comando *sudo -i* e digite a sua senha.  


Após isso adicione seu usuário ao grupo do docker para não precisar ficar usando o sudo antes dos comandos. Para isso siga as etapas abaixo:  

Para criar e adicionar o user em um grupo docker
```
sudo groupadd docker
```
Em caso de ja ter o grupo continue para o próximo passo.  
```
sudo gpasswd -a ${USER} docker
```
Depois reinicie o container :
```
sudo service docker restart
```
Agora abra uma nova sessão
```
newgrp - docker
```
---