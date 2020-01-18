## DockerFile, DockerFile, e mais DockerFiles!
Instrução de como buildar a imagem do docker que iremos construir.  
A primeira etapa é ir até o diretório onde esta o primeiro dockerfile. 
```
sudo cd /root/primeiro_dockerfile/
```
Para acessar o Dockerfile, use o editor vi ou o nano:  
```
vi Dockerfile
```
### Parâmetros
Aqui teremos uma visão geral dos parâmetros do dockerfile.  

**ADD**: Pega um arquivo e joga do host docker para um container/imagem. Exemplo ADD eai.txt /diretorio/  

**CMD**: São parametros para o entrypoint do container, Se meu entrypoint é um bash todo comando que eu adicionar no CMD deve interagir com o bash. Exemplo: CMD ["sh", "-c", "echo", "$HOME"]  

**LABEL**: Adiciona metadados para o container, isso ajuda a gerenciar os containers. Exemplo LABEL Description="Bla Bla Bla"  

**COPY**: Copia os arquivos ou diretório, sua diferença para o ADD é que o ADD consegue jogar arquivos empacotados também. Exemplo: COPY opa.txt /diretorio/  

**ENTRYPOINT**: Permite deixar que um processo seja o principal processo dentro do container, se esse processo morre o container morre. Exemplo: ENTRYPOINT ["usr/bin/apache2ctl","-D","FOREGROUND"], imagine que queremos monitorar os processos do apache, se o pache morrer o container morre. Se eu crio um entrypoint o CMD será um parametro para ele.   

**ENV**: Environment, permite criar variaveis de ambiente para o container. Exemplo: ENV meunome = "Diogo"  

**EXPOSE**: Permite selecionar uma porta do container a ser exposta. Exemplo: EXPOSE 80  

**FROM**: Qual a imagem de base para montar a minha imagem. Exemplo: FROM debian. usa a imagem debian para montar a minha imagem, obs.: deve ser a primeira opção a ter no dockerfile.  

**RUN**: Serve para executar comandos no container, como instalar pacotes. Obs.: quanto menos RUN melhor por terá menos camadas. Uma dica é concatenar varios comandos no run (usando o &&). Exemplo: RUN apt-get update && apt-get install apache2 && apt-get clean  
Obs.: O clean não limpa o espaço quando se tem 
varias camadas, por exemplo se fosse executado cada apt-get em uma camada diferente.  

**USER**: Indica o usuário default que executará a imagem. Se nenhum for passado ele usará o root (cuidado com isso!). Exemplo: USER diogo  

**WORKDIR**: Faz com que o diretorio indicado será o raiz do container, o diretorio de trabalho do container. Exemplo WORKDIR /diretorio

**VOLUME**: O volume a ser utilizado para o container. Exemplo: VOLUME /diretorio_volume/

**MAINTAINER**: Quem escreveu o dockerfile. Obs.: O mainteiner fica abaixo do FROM (seria a segunda linha) Exemplo: MAINTAINER Diogo
