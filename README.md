Biblioteca API — Documentação Completa

🔗 Base URL http://localhost:3000/api

🔐 Autenticação A API utiliza autenticação via Bearer Token. Header obrigatório: Authorization: Bearer {token}

Manual da API
📖 Books

🔹 GET /books Descrição: Retorna uma lista paginada de livros. Parâmetros (query): Nome Tipo Obrigatório Descrição page number ❌ Página atual limit number ❌ Quantidade por página

Exemplo de requisição: GET /books?page=1&limit=10 Resposta 200: [ { "id": 1, "title": "Dom Casmurro", "author": "Machado de Assis", "available": true } ]

🔹 GET /books/{id} Descrição: Retorna um livro específico. Resposta 200: { "id": 1, "title": "Dom Casmurro", "author": "Machado de Assis", "available": true } Erro 404: { "status": "error", "message": "Livro não encontrado" }

🔹 POST /books Descrição: Cria um novo livro. Body: { "title": "1984", "author": "George Orwell" } Resposta 201

🔹 PUT /books/{id} Atualiza um livro existente.

🔹 DELETE /books/{id} Remove um livro.

👤 Users

🔹 GET /users Lista todos os usuários.

🔹 POST /users Cria usuário. { "fullName": "João Silva", "email": "joao@email.com
" }

🔹 GET /users/{id} Retorna usuário específico.

🔄 Loans

🔹 GET /loans Lista empréstimos.

🔹 POST /loans Cria empréstimo. { "userId": 1, "bookId": 2, "dueDate": "2026-05-01" }

🔹 PUT /loans/{id}/return Marca como devolvido.

⚠️ Padrão de Erros { "status": "error", "message": "Descrição do erro" }

Guia de Instalação e Configuração
Requisitos Node.js (>= 18) npm ou yarn Git

🚀 Instalação git clone https://github.com/GabrielLosekann-desenvolvedor/Biblioteca-API/blob/main/openapi.yaml
 cd biblioteca-api npm install

▶️ Execução npm start

🌐 Acesso http://localhost:3000/api

⚙️ Variáveis de Ambiente (exemplo) PORT=3000 NODE_ENV=development

Guia de Uso para Desenvolvedores
🔁 Fluxo completo de uso Criar usuário Listar livros Criar empréstimo Devolver livro

📌 JavaScript (Fetch) // Criar usuário await fetch('/users', { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify({ fullName: 'João', email: 'joao@email.com
' }) })

// Listar livros const books = await fetch('/books').then(r => r.json())

// Criar empréstimo await fetch('/loans', { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify({ userId: 1, bookId: 2, dueDate: '2026-05-01' }) })

🐍 Python (Requests) import requests

Listar livros
res = requests.get('http://localhost:3000/api/books
') print(res.json())

Criar empréstimo
requests.post('http://localhost:3000/api/loans
', json={ "userId": 1, "bookId": 2, "dueDate": "2026-05-01" })

📌 Casos de Uso Sistema de biblioteca escolar Plataforma educacional Controle de empréstimos corporativos Integração com apps mobile

Histórico de Versões (Changelog)
🔹 v1.0.0 Criação da API Endpoints de livros e usuários

🔹 v1.1.0 Adicionado sistema de empréstimos Melhorias de validação

🔹 v2.0.0 (Breaking Change) Campo name → fullName Impacto: Clientes antigos deixam de funcionar. Migração: Atualizar payloads: { "fullName": "João Silva" }

Plano de Manutenção
📌 Estratégia Atualizar documentação a cada release Sincronizar com mudanças no código Revisão contínua

⚠️ Depreciação Marcar endpoint como deprecated Informar prazo (ex: 6 meses) Remover na próxima versão major

📊 Versionamento (SemVer) Formato: MAJOR.MINOR.PATCH MAJOR → quebra compatibilidade MINOR → nova funcionalidade PATCH → correção

🔄 Evolução da API Exemplo: v1 → livros e usuários v2 → empréstimos v3 → reservas (futuro)
