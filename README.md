# Guia rápido para você levantar o projeto. Ele é dividido em duas partes:

Backend (o "cérebro"): Feito em Spring Boot (Java), que cuida dos dados.
Frontend (o "rosto"): Feito em Vue, que é o site bonito que você vê no navegador.

Precisa: 
Java (versão 21 ou mais nova)

Maven (para o backend)

Node.js e npm (para o frontend)

1. Backend:
O backend vai rodar na porta (http://localhost:8088).

Abra seu terminal (como o PowerShell).

Pare qualquer processo Java que esteja usando essa porta.

Vá até a pasta do backend:

PowerShell

cd 'C:\Users\User\Downloads\lista de tarefas\backend'
Compile o projeto (isso "empacota" o código para rodar):

PowerShell

mvn -DskipTests package
Inicie o servidor:

PowerShell

java -jar .\target\api-0.0.1-SNAPSHOT.jar
Alternativa mais rápida: Se preferir, em vez dos passos 4 e 5, você pode só rodar mvn spring-boot:run.

Deixe esse terminal aberto e rodando!


2. Frontend:
O frontend vai rodar na porta (http://localhost:5173).

Abra outro terminal e deixe sempre o backend rodando.

Vá até a pasta do frontend:

PowerShell

cd 'C:\Users\User\Downloads\lista de tarefas\frontend'
Se for a primeira vez, instale as dependências dele:

PowerShell

npm install
Inicie o site:

PowerShell

npm run dev

Acessar no navegador (http://localhost:5173).