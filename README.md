# ISA-Frontend

## Keycloak
Para executar o Frontend é necessário estar com uma instância do Keycloak em execução.
A configuração utilizada é fornecida pelo repositório ISA-Backend.

## Dependências
Para a instalação das dependências da aplicação é necessário executar o comando citada abaixo na pasta raiz da aplicação:
```
npm install
```
logo após execute o comando para fazer o build do projeto:
``` 
npm run build
```
## Buildando e rodando o container
A inicialização do projeto pode ser feita de dois modos:
1. Utilizando containers prontos e disponibilizados pelo projeto 
2. Realizando a sua construção localmente

Os dois modos serão apresentados a seguir:

### 1. Utilizando Containers 
```
docker build -t isa-frontend .
```
* Uso de imagem disponibilizada *
UNDER CONSTRUCTION

* Inicialização do container *

```
docker run \
       --network isa-net \
       -d -p 80:80 \
       -e REACT_APP_API_URL="http://localhost:3333" \
       -e REACT_APP_KEYCLOAK_SERVER_URL="http://$(hostname -I | awk '{print $1}'):8080/auth" \
       -e REACT_APP_KEYCLOAK_CLIENT="isa-frontend" \
       -e REACT_APP_KEYCLOAK_REALM="isa-qualis" \
        --name isa-frontend \
          isa-frontend
```
As variáveis API_URL e KEYCLOAK_SERVER_URL devem ser preenchidas com o ip das mesmas na network criada, descritas no Isa-Backend

### 2. Opção em ambiente de desenvolvimento com start

para rodar o projeto em ambiente de desenvolvimento, sem container, execute o seguinte comando:
```
REACT_APP_KEYCLOAK_SERVER_URL="http://$(hostname -I | awk '{print $1}'):8080/auth" REACT_APP_KEYCLOAK_CLIENT="isa-frontend" REACT_APP_KEYCLOAK_REALM="isa-qualis" REACT_APP_API_URL="http://localhost:3333/"  npm start
```
