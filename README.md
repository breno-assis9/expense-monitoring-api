# Expense Monitoring API

A **Expense Monitoring API** é uma API RESTful robusta e segura, desenvolvida com **.NET Core 8** e **SQL Server**, projetada para gerenciar as finanças pessoais de maneira simples e eficiente. Com a integração de diversas tecnologias, como **AutoMapper**, **Elmah**, **JWT Bearer Authentication**, **FluentValidation**, **Swagger**, e **Entity Framework Core**, essa API oferece uma experiência de alto nível para desenvolvedores e usuários finais.

---

## 🚀 Tecnologias Utilizadas

- **.NET Core 8**: Framework para construção de APIs modernas e escaláveis.
- **SQL Server**: Banco de dados relacional utilizado para armazenamento seguro de dados.
- **AutoMapper**: Mapeamento automático entre objetos e DTOs, reduzindo a complexidade do código.
- **Elmah**: Ferramenta de logging e monitoramento de erros para garantir a confiabilidade da aplicação.
- **JWT Bearer Authentication**: Autenticação baseada em tokens JWT, garantindo um controle de acesso seguro.
- **Entity Framework Core**: ORM para facilitar a manipulação de dados no banco de dados.
- **FluentValidation**: Validação de dados com uma API fluente, garantindo a consistência das informações recebidas.
- **Swagger**: Documentação interativa da API, permitindo testes diretos e fácil integração.

---

## 💡 Funcionalidades

- **Cadastro de Despesas**: Possibilidade de criar, editar e excluir despesas pessoais.
- **Relatórios de Gastos**: Visualização de relatórios detalhados através de gráficos e tabelas.
- **Autenticação JWT**: Controle de acesso seguro com tokens JWT.
- **Validação de Dados**: Garantia de dados consistentes com FluentValidation.
- **Monitoramento de Erros**: Detecção e registro de erros em tempo real via Elmah.
- **Documentação Swagger**: Interface interativa para explorar e testar a API.
- **Versionamento de API**: Suporte a múltiplas versões da API para retrocompatibilidade.

---

## 📦 Como Começar

### Pré-requisitos

Para rodar a aplicação localmente, você precisará ter as seguintes ferramentas instaladas:

- **.NET Core SDK 8.x** ou superior
- **SQL Server** (local ou remoto)
- **Postman** ou outro cliente de API (opcional)

### Passos para Configuração

1. **Clone o repositório**:

   git clone https://github.com/seu-usuario/expense-monitoring-api.git
   cd expense-monitoring-api
   
2. **Restaurar dependências:**

dotnet restore
Configuração do Banco de Dados:

3. **Configure a string de conexão do SQL Server no arquivo appsettings.json:**

"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=ExpenseDB;Trusted_Connection=True;"
}

4. **Executar Migrations:**

Se for a primeira vez que você está rodando a aplicação, será necessário aplicar as migrações do banco de dados:

dotnet ef database update

5. **Rodar a aplicação:**

Execute o seguinte comando para iniciar a API:


dotnet run
A aplicação estará disponível em http://localhost:5000.

## 🛠️ Endpoints da API
Acesse a documentação da API interativamente pelo Swagger. Para visualizar a documentação, acesse o seguinte endereço:

**URL do Swagger:** http://localhost:5000/swagger
Aqui você poderá testar diretamente todos os endpoints da API, verificar os parâmetros esperados, e visualizar as respostas.

**Exemplos de Endpoints:**
Autenticação:

POST /api/auth/login
Retorna um token JWT para autenticação.

**Cadastro de Despesas:**

POST /api/v1/expenses
Adiciona uma nova despesa.

**Relatórios de Gastos:**

GET /api/v1/expenses/report
Gera um relatório de todas as despesas.

## ✅ Validação de Dados com FluentValidation
A API utiliza o FluentValidation para validar as entradas dos usuários, garantindo que os dados enviados sejam válidos e consistentes. A seguir, um exemplo de como as validações são feitas para o modelo de despesa:

public class ExpenseValidator : AbstractValidator<ExpenseDto>
{
    public ExpenseValidator()
    {
        RuleFor(x => x.Amount).GreaterThan(0).WithMessage("O valor deve ser maior que zero.");
        RuleFor(x => x.Category).NotEmpty().WithMessage("A categoria é obrigatória.");
    }
}

## 🔧 Monitoramento de Erros com Elmah
Elmah é utilizado para registrar erros não tratados na aplicação. O registro dos erros pode ser visualizado acessando a URL /elmah.axd (caso configurado corretamente) após rodar a aplicação. Isso facilita a identificação e correção rápida de falhas.

## 🔐 Autenticação JWT
A API utiliza JWT Bearer Tokens para autenticação. Para obter um token de acesso, envie as credenciais do usuário para o endpoint de login:

**Endpoint de Login:**

POST /api/auth/login
Exemplo de Resposta:

{
  "token": "seu-token-jwt-aqui"
}
Inclua o token nas requisições subsequentes utilizando o cabeçalho Authorization:

**Authorization:** Bearer seu-token-jwt-aqui

## 📈 Versionamento de API
A API suporta versionamento de forma que você pode ter várias versões da mesma, garantindo a retrocompatibilidade. Os endpoints podem ser acessados com diferentes versões de forma simples:

**Exemplo de versões de endpoints:**

GET /api/v1/expenses
GET /api/v2/expenses

## 📝 Contribuindo

Contribuições são bem-vindas! Se você encontrou um bug ou tem sugestões de melhorias, por favor, siga os passos abaixo para contribuir:

Fork este repositório.
Crie uma branch para sua feature ou correção:
git checkout -b feature/MinhaFeature
Faça as alterações necessárias e comite-as:
git commit -am 'Adiciona nova funcionalidade'
Envie para o seu fork:
git push origin feature/MinhaFeature
Abra um Pull Request explicando suas alterações.

## 🛡️ Licença
Distribuído sob a licença MIT. Veja o arquivo LICENSE para mais informações.

## 🙏 Agradecimentos
Agradecemos a todos os mantenedores e à comunidade de código aberto pelas ferramentas e bibliotecas que tornam este projeto possível. Nosso objetivo é fornecer uma solução robusta e fácil de usar para o controle de despesas pessoais.


