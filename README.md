⚙️ Arquitetura

Stack Principal

Backend: C# ASP.NET Core

Frontend: Angular

Organização Geral

Separação clara entre frontend e backend

Comunicação via APIs RESTful

Integrações e Configurações

API REST (Mock)

Endpoint: POST /login

Comportamento:

Recebe JSON com { Username, Password }

Se usuário for admin e senha password, retorna token mock { token: "mock-jwt-token-123" }

Caso contrário, retorna status 401 Unauthorized

CORS habilitado para qualquer origem, método e header para suportar Angular frontend

Angular

LoginComponent

Campos bindados: username, password

Método login() faz requisição POST para http://localhost:5000/login

Sucesso: armazena token no localStorage e navega para /dashboard

Falha: mostra mensagem de erro "Invalid credentials"

DashboardComponent

Componente simples, vazio por enquanto

Acessado após login bem-sucedido

AppComponent

No ngOnInit(), verifica se token existe no localStorage

Se não existir, seta token mock mock-jwt-token-123

Facilita testes locais sem passar pelo login toda vez

Testes com Jasmine

Framework padrão para testes unitários Angular

Já incluído por padrão em projetos Angular CLI

Utilizado para:

Testar componentes (ex: LoginComponent, DashboardComponent)

Verificar lógica de navegação, validação e manipulação de dados locais (ex: localStorage)

Estrutura básica de um teste:

describe('LoginComponent', () => {
  it('deve armazenar token no login com sucesso', () => {
    // lógica do teste
  });
});

🚧 TODO/Futuras Features

StatusDescrição



✅

Configurar REST básico em ASP.NET Core com rota POST /login

✅

Implementar frontend Angular para login

✅

Criar componente básico Dashboard

✅

Inicializar token mock no localStorage no AppComponent

✅

Adicionar Jasmine para testes unitários

❌

Implementar proteção de rota para Dashboard (guardas Angular)

❌

Implementar autenticação via localStorage com validação e proteção de rotas
