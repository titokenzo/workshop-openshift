# Lab 01 - Desmistificando Infra Docker

Primeiro passo é entender como Docker funciona e seus principais componentes.

## 1 - Instalação do Docker {#_1_instala_o_do_docker}

```text
yum install docker 

systemctl start docker
```

|  | Instala docker |
| :--- | :--- |
|  | Sobe Docker |

## 2 - Lista Imagens Docker {#_2_lista_imagens_docker}

```text
docker images
```

|  | Lista as imagens locais do Docker |
| :--- | :--- |


## Criando um Docker file {#_criando_um_docker_file}

```text
mkdir helloworld
cd helloworld
echo "FROM php:7.0-apache" >> Dockerfile
```

|  | Fonte:[https://hub.docker.com/\_/php/](https://hub.docker.com/_/php/) |
| :--- | :--- |


## Construindo Imagem {#_construindo_imagem}

```text
docker build -t helloworld .
```

|  | Verifique as camadas da imagem. |
| :--- | :--- |


## Listando as Imagens {#_listando_as_imagens}

```text
docker images
```

## Subindo o container {#_subindo_o_container}

```text
docker run -d --name helloworld helloworld
docker ps
```

## Entrando no Container {#_entrando_no_container}

```text
docker exec -it <id container> /bin/bash
```

 

