## Remoção de imagens

Muitas vezes é necessário remover as imagens e os containers, para isso você pode usar os comandos *docker rm {nome do container}* ou *docker rmi {nome da imagem}*. As vezes pode ocorrer problemas de dependências para a remoção, daí você tem de usar o paramêtro *-f* para forçar a remoção. 

Por exemplo apra remover todos os containers: 
```
docker rm $(docker ps -a -f status=exited -f status=created -q)
```
Para remover todas as imagens: 
```
docker rmi $(docker images -a -q)
```
O artigo da [digital ocean](https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes) tem uma ótima referência para realizar as remoções.  

---