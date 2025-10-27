# Instalação do repositório

Instalação do Omeka containerizado para facilitar a instalação em outros ambientes.
Além da presença do banco de dados MySQL pronto para trabalho.

## Subindo os containers de execução

Clonando o repositório e acessando seu projeto:
```git
  git clone git@github.com:guzztavo2/omeka.git
```
```bash
   cd omeka/
```
---
Subir o container com o seguinte comando:
```bash
   docker-compose up -d --build
```
---
Após a instalação e execução dos containers, você consegue acessa-los com o seguinte comando:
```bash
docker exec -it omeka_app bash
```
Dentro do container, você conseguirá ver arquivos principais que estarão rodando no container
```bash
cd /var/www/html
```
Realize todas as intalações iniciais com os comandos abaixo:
```bash
npm install
```
```bash
npx gulp init
```
Lembre-se de configurar também o banco de dados:
omeka/config/database.ini:
```bash
user     = "omeka"
password = "omeka"
dbname   = "omeka"
host     = "db"
```
*Importante salientar:* O host tem que ser explicitamente definido como "db", que é o nome definido na aplicação do docker-compose.yml. Para caso de já está executando um segundo banco de dados na máquina.
---
As configurações representantes podem ser identificados no seguinte diretorio do projeto:
./docker-compose.yml
Dentro da aplicação do DB no docker-compose você pode identificar as configurações de ambientes e serem alterados na maneira que precisar:
```bash
environment:
MYSQL_ROOT_PASSWORD: root
MYSQL_DATABASE: omeka
MYSQL_USER: omeka
MYSQL_PASSWORD: omeka
```

### Problema de permissão
Caso o sistema de algum problema na permissão, basta executar o comando abaixo:
````bash
chmod -R 777 omeka/files
````

