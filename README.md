# Projeto: Lista de Tarefas (Spring Boot + Vue) 

Localmente uma API em Spring Boot (backend) e uma interface em Vue (frontend). Este README é curto, direto e mostra como rodar e testar rapidamente.

---

- backend/: API em Spring Boot (Java + Maven)
- frontend/: App cliente em Vue (Vite + axios)

Pré-requisitos (rápido)
- Java 21+ instalado
- Maven (mvn) instalado no PATH
- Node.js + npm instalados

Portas padrão
- Backend: http://localhost:8088 com context-path `/api` (ex.: http://localhost:8088/api/tarefas)
- Frontend (dev): http://localhost:5173

Rápido — rodando localmente (Windows PowerShell)

Backend
1) Pare qualquer processo Java antigo (se houver). Substitua o PID conforme necessário:

```powershell
Stop-Process -Id 18116 -Force
```

2) Compilar e empacotar (gera o JAR atualizado):

```powershell
cd 'C:\Users\User\Downloads\lista de tarefas\backend'
mvn -DskipTests package
```

3) Iniciar o JAR:

```powershell
java -jar .\target\api-0.0.1-SNAPSHOT.jar
```

Alternativa (rodar direto do código, precisa ter mvn):

```powershell
mvn spring-boot:run
```

Frontend
1) Abrir um novo terminal e instalar dependências (só na primeira vez):

```powershell
cd 'C:\Users\User\Downloads\lista de tarefas\frontend'
npm install
```

2) Rodar o servidor de desenvolvimento (Vite):

```powershell
npm run dev
# acesse: http://localhost:5173
```

Como verificar que está funcionando

- Teste preflight (OPTIONS):

```powershell
curl.exe -i -X OPTIONS -H "Origin: http://localhost:5173" -H "Access-Control-Request-Method: GET" "http://localhost:8088/api/tarefas"
```

Deve retornar `HTTP/1.1 200` com cabeçalhos `Access-Control-Allow-*`.

- Teste GET (esperado: JSON de tarefas):

```powershell
curl.exe -i -H "Origin: http://localhost:5173" "http://localhost:8088/api/tarefas"
```

Se retornar JSON, o frontend também conseguirá carregar a lista.

Notas importantes (leitura rápida)
- CORS: durante o desenvolvimento foi adicionada uma configuração permissiva para permitir chamadas do Vite (localhost:5173). Para produção, harmonize/fortaleça a política de CORS — evite `allowedOrigins("*")` com credenciais habilitadas.
- Context-path e controllers: o projeto usa `server.servlet.context-path=/api`. Mantenha os controllers com mapeamento sem `/api` (ex.: `@RequestMapping("/tarefas")`) para evitar `/api/api`.

Onde olhar no código
- Backend: `backend/src/main/java/br/com/tarefas/api` (controller, service, repository, config)
- Frontend: `frontend/src` e `frontend/src/services/tarefaService.js` (baseURL)

