<div align="center">

# 🦅 Transformese - Gerando Falcões

### Sistema Corporativo de Gestão de Candidatos para Programas Sociais

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet)](https://dotnet.microsoft.com/)
[![C#](https://img.shields.io/badge/C%23-12.0-239120?logo=csharp)](https://docs.microsoft.com/en-us/dotnet/csharp/)
[![Entity Framework](https://img.shields.io/badge/EF%20Core-8.0.11-512BD4)](https://docs.microsoft.com/en-us/ef/)
[![SQL Server](https://img.shields.io/badge/SQL%20Server-LocalDB-CC2927?logo=microsoft-sql-server)](https://www.microsoft.com/sql-server)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?logo=bootstrap)](https://getbootstrap.com/)
[![JWT](https://img.shields.io/badge/JWT-Auth-000000?logo=json-web-tokens)](https://jwt.io/)
[![Swagger](https://img.shields.io/badge/Swagger-OpenAPI-85EA2D?logo=swagger)](https://swagger.io/)

</div>

---

## 📋 Resumo Executivo

**Transformese** é uma solução enterprise de gestão de candidatos desenvolvida para a organização social [**Gerando Falcões**](https://gerandofalcoes.com/), que transforma realidades através da educação, tecnologia e desenvolvimento social.

### 🎯 Propósito

Centralizar e otimizar o processo de inscrição, triagem e gestão de candidatos para programas sociais e cursos de capacitação profissional, garantindo escalabilidade, rastreabilidade e transparência no processo seletivo.

### 💡 Valor Agregado

- **Centralização**: Unifica múltiplos canais de inscrição em uma única plataforma
- **Automação**: Reduz processos manuais de triagem e validação
- **Rastreabilidade**: Acompanha status de candidatos em tempo real
- **Escalabilidade**: Arquitetura preparada para crescimento orgânico
- **Governança**: Controles de acesso e auditoria integrados
- **Multi-Interface**: API REST, Web (MVC) e Desktop (WinForms)

---

## 🏗️ Arquitetura e Stack Tecnológica

### Arquitetura de Software

O projeto implementa **Clean Architecture** com separação clara de responsabilidades em camadas:

```
┌─────────────────────────────────────────────────────────┐
│              UI Layer (MVC/Desktop)                      │
├─────────────────────────────────────────────────────────┤
│              API Layer (Controllers)                     │
├─────────────────────────────────────────────────────────┤
│         Application Layer (Services/Repositories)        │
├─────────────────────────────────────────────────────────┤
│            Domain Layer (Entities/Enums)                 │
├─────────────────────────────────────────────────────────┤
│       Infrastructure Layer (EF Core/DbContext)           │
└─────────────────────────────────────────────────────────┘
```

**Padrões Arquiteturais:**
- ✅ **Domain-Driven Design (DDD)** - Entidades isoladas na camada de domínio
- ✅ **Repository Pattern** - Abstração da camada de persistência
- ✅ **Dependency Injection** - Inversão de controle via DI nativo do .NET
- ✅ **RESTful API** - Endpoints padronizados com versionamento implícito

---

### Stack Tecnológica

#### Backend

| Tecnologia | Versão | Finalidade |
|------------|--------|------------|
| **.NET SDK** | 8.0 | Framework principal para desenvolvimento web e desktop |
| **Entity Framework Core** | 8.0.11 | ORM para mapeamento objeto-relacional e migrations |
| **SQL Server / LocalDB** | Latest | Banco de dados relacional para persistência |
| **JWT Bearer Authentication** | 8.0.0 | Autenticação e autorização baseada em tokens |
| **AutoMapper** | 12.0.0 | Mapeamento automático entre entidades e DTOs |
| **Swagger/OpenAPI** | 6.5.0 | Documentação interativa de API |
| **System.IdentityModel.Tokens.Jwt** | 8.15.0 | Geração e validação de tokens JWT |

#### Frontend Web (MVC)

| Tecnologia | Versão | Finalidade |
|------------|--------|------------|
| **ASP.NET MVC** | .NET 8 | Framework web MVC para renderização server-side |
| **Bootstrap** | 5.3 | Framework CSS para UI responsiva |
| **jQuery** | 3.x | Biblioteca JavaScript para manipulação DOM |
| **jQuery Validation** | Latest | Validação client-side de formulários |

#### Desktop

| Tecnologia | Versão | Finalidade |
|------------|--------|------------|
| **Windows Forms** | .NET 8 | Interface desktop nativa para Windows |
| **HttpClient** | Built-in | Comunicação HTTP com API REST |

---

### Dependências Principais

**Transformese.Api:**
```xml
<PackageReference Include="Microsoft.AspNetCore.Authentication.JwtBearer" Version="8.0.0" />
<PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="8.0.11" />
<PackageReference Include="Swashbuckle.AspNetCore" Version="6.5.0" />
<PackageReference Include="AutoMapper.Extensions.Microsoft.DependencyInjection" Version="12.0.0" />
```

**Transformese.Data:**
```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="8.0.11" />
<PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="8.0.11" />
<PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="8.0.11" />
```

---

## 📁 Estrutura do Repositório

A solução segue uma organização modular em 5 projetos independentes:

```
📁 GerandoFalcoes/
│
├── 📄 TransformeseSolution.sln          # Solução Visual Studio
├── 📄 .gitignore                        # Exclusões de versionamento
├── 📄 LEIA-ME.txt                       # Instruções originais (legacy)
│
├── 📁 Transformese.Domain/              # 🎯 Camada de Domínio
│   ├── 📁 Entities/
│   │   ├── BaseEntity.cs                # Entidade base com ID comum
│   │   └── Candidato.cs                 # Entidade principal (candidatos)
│   ├── 📁 Enums/
│   │   └── StatusCandidato.cs           # Enum de status (Inscrito, Aprovado, etc.)
│   └── Transformese.Domain.csproj
│
├── 📁 Transformese.Data/                # 💾 Camada de Dados
│   ├── ApplicationDbContext.cs          # DbContext do Entity Framework
│   ├── ApplicationDbContextFactory.cs   # Factory para design-time migrations
│   ├── 📁 Repositories/
│   │   └── CandidatoRepository.cs       # Repositório de candidatos
│   ├── 📁 Migrations/                   # Migrations do EF Core
│   └── Transformese.Data.csproj
│
├── 📁 Transformese.Api/                 # 🌐 API REST
│   ├── 📁 Controllers/
│   │   └── CandidatosController.cs      # Endpoints de candidatos (/api/candidatos)
│   ├── 📁 DTOs/                         # Data Transfer Objects (planejado)
│   ├── Program.cs                       # Configuração da API (DI, JWT, CORS)
│   ├── appsettings.json                 # Configurações (ConnectionString, JWT)
│   └── Transformese.Api.csproj
│
├── 📁 Transformese.MVC/                 # 🌍 Frontend Web (ASP.NET MVC)
│   ├── 📁 Controllers/
│   │   ├── HomeController.cs            # Controller da home
│   │   └── InscricaoController.cs       # Controller de inscrições
│   ├── 📁 Views/                        # Razor Views (.cshtml)
│   │   ├── Home/
│   │   ├── Inscricao/
│   │   └── Shared/
│   ├── 📁 Services/                     # Serviços HTTP (ApiService)
│   ├── 📁 ViewModels/                   # ViewModels para Views
│   ├── 📁 wwwroot/                      # Assets estáticos (CSS, JS, images)
│   │   ├── css/
│   │   ├── js/
│   │   └── lib/                         # Bibliotecas (Bootstrap, jQuery)
│   ├── Program.cs
│   ├── appsettings.json
│   └── Transformese.MVC.csproj
│
├── 📁 Transformese.Desktop/             # 🖥️ Aplicação Desktop (WinForms)
│   ├── Login.cs                         # Formulário de Login
│   ├── Login.Designer.cs                # Designer do formulário
│   ├── Dashboard.cs                     # Dashboard principal
│   ├── Dashboard.Designer.cs
│   ├── Program.cs                       # Entry point
│   ├── 📁 Resources/                    # Recursos (imagens, ícones)
│   └── Transformese.Desktop.csproj
│
└── 📁 Transformese.Web/                 # 🌐 MVC Alternativo (cursos/unidades)
    ├── 📁 Controllers/                  # Controllers de Cursos, Unidades, etc.
    └── Transformese.Web.csproj
```

### Lógica de Organização

- **Separação por camadas**: Domain (regras de negócio) → Data (persistência) → API (exposição) → UI (apresentação)
- **Independência de frameworks**: Domain não possui dependências externas
- **Testabilidade**: Cada camada pode ser testada isoladamente
- **Reutilização**: Domain e Data são compartilhados entre API, MVC e Desktop

---

## ✨ Funcionalidades-Chave

### 🔹 API REST (`Transformese.Api`)

| Feature | Endpoint | Descrição |
|---------|----------|-----------|
| **Inscrição de Candidatos** | `POST /api/candidatos/inscrever` | Registra novo candidato com validação de CPF único |
| **Autenticação JWT** | *(planejado)* `POST /api/auth/login` | Gera token de acesso para autenticação |
| **Documentação Swagger** | `GET /swagger` | Interface interativa para testar endpoints |
| **CORS Configurado** | Global | Permite consumo por frontends externos |

**Validações Implementadas:**
- ✅ CPF obrigatório e único (verifica duplicidade no banco)
- ✅ Normalização de CPF (remove pontos e hífens)
- ✅ Reference Cycle Handling (evita loops em JSON)
- ✅ Retorno padronizado de erros (BadRequest, Conflict)

---

### 🔹 Frontend Web (`Transformese.MVC`)

- ✅ **Formulário de Inscrição**: Interface responsiva com campos completos (dados pessoais, contato, socioeconômicos)
- ✅ **Validação Client-Side**: jQuery Validation para feedback imediato
- ✅ **Integração com API**: HttpClient service para comunicação com backend
- ✅ **Design Responsivo**: Bootstrap 5 para mobile-first

---

### 🔹 Desktop (`Transformese.Desktop`)

- ✅ **Interface de Login**: Autenticação visual (Windows Forms)
- ✅ **Dashboard de Gestão**: Painel para visualização e gestão de candidatos
- ✅ **Consumo de API REST**: Comunicação via HttpClient

---

### 🔹 Domínio (`Transformese.Domain`)

**Entidade `Candidato`:**
```csharp
public class Candidato : BaseEntity
{
    // Dados Pessoais
    public string NomeCompleto { get; set; }
    public string CPF { get; set; }
    public DateTime DataNascimento { get; set; }
    
    // Contato
    public string Email { get; set; }
    public string Telefone { get; set; }
    
    // Dados Socioeconômicos (Requisito Gerando Falcões)
    public string Cidade { get; set; }
    public string Estado { get; set; }
    public bool PossuiComputador { get; set; }
    public bool PossuiInternet { get; set; }
    public string? PerfilLinkedin { get; set; }
    
    // Controle de Processo
    public DateTime DataCadastro { get; set; }
    public StatusCandidato Status { get; set; }
    public int? UnidadeId { get; set; }
}
```

**Enum `StatusCandidato`:**
- `Inscrito` → Candidato recém-inscrito
- `EmAnalise` → Em processo de triagem
- `Aprovado` → Aceito no programa
- `Reprovado` → Não aceito

---

## 🚀 Guia de Instalação e Execução

### Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- ✅ [**.NET 8 SDK**](https://dotnet.microsoft.com/download/dotnet/8.0) - Verifique com `dotnet --version`
- ✅ **SQL Server LocalDB** ou SQL Server Developer Edition ([Download aqui](https://www.microsoft.com/sql-server/sql-server-downloads))
- ✅ **Visual Studio 2022+** (recomendado) ou VS Code com C# Extension
- ✅ **Git** para clonar o repositório

---

### Instalação Passo a Passo

#### 1️⃣ Clone o Repositório

```bash
git clone https://github.com/seu-usuario/GerandoFalcoes.git
cd GerandoFalcoes
```

#### 2️⃣ Restaure as Dependências

```bash
dotnet restore
```

#### 3️⃣ Configure a Connection String

Edite o arquivo `Transformese.Api/appsettings.json`:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\MSSQLLocalDB;Database=TransformeseDB-Api;Trusted_Connection=True;TrustServerCertificate=True;"
  }
}
```

> **Nota**: Ajuste o servidor caso não esteja usando LocalDB. Para SQL Server padrão, use:
> ```
> "Server=localhost;Database=TransformeseDB;User Id=seu_usuario;Password=sua_senha;TrustServerCertificate=True;"
> ```

#### 4️⃣ Instale o EF Core CLI (se necessário)

```bash
dotnet tool install --global dotnet-ef
```

Verifique a instalação:
```bash
dotnet ef --version
```

#### 5️⃣ Crie o Banco de Dados

Execute as migrations para criar o banco automaticamente:

```bash
cd Transformese.Api
dotnet ef database update --project ../Transformese.Data/Transformese.Data.csproj
```

> **Alternativa**: Se já existem migrations, apenas rode `dotnet ef database update`.

#### 6️⃣ Execute a API

```bash
dotnet run --project Transformese.Api
```

A API estará disponível em:
- 🌐 **HTTPS**: `https://localhost:5001`
- 🌐 **HTTP**: `http://localhost:5000`
- 📘 **Swagger**: `https://localhost:5001/swagger`

#### 7️⃣ Execute o Frontend MVC (Em outro terminal)

```bash
dotnet run --project Transformese.MVC
```

Acesse no navegador: `https://localhost:7xxx` (porta exibida no terminal)

#### 8️⃣ Execute o Desktop (Via Visual Studio)

1. Abra `TransformeseSolution.sln` no Visual Studio
2. Clique com botão direito em `Transformese.Desktop` → **Set as Startup Project**
3. Pressione `F5` para executar

---

### Configurações Adicionais

#### Variáveis de Ambiente / Configurações

**JWT (appsettings.json):**
```json
"Jwt": {
  "Key": "minha-chave-secreta-aqui-123456789",
  "Issuer": "Transformese.Api",
  "Audience": "Transformese.Api",
  "ExpiresMinutes": "120"
}
```

> ⚠️ **IMPORTANTE**: Altere a chave JWT em produção! Use Azure Key Vault ou variáveis de ambiente seguras.

---

### Troubleshooting

**Erro: "Trust certificate HTTPS"**
```bash
dotnet dev-certs https --trust
```

**Erro: "The ConnectionString property has not been initialized"**
- Verifique se `appsettings.json` está configurado corretamente
- Confirme que o SQL Server está rodando

**Erro: "A network-related or instance-specific error"**
- Verifique se o SQL Server LocalDB está instalado
- Execute: `sqllocaldb start MSSQLLocalDB`

---

## 🤝 Como Contribuir

Contribuições são bem-vindas! Siga o processo abaixo para colaborar:

### Branching Strategy

| Branch | Finalidade | Proteção |
|--------|-----------|----------|
| `main` | Código em produção | ✅ Protegida (requer PR aprovado) |
| `develop` | Código em desenvolvimento | ✅ Protegida |
| `feature/<nome>` | Novas funcionalidades | - |
| `fix/<nome>` | Correções de bugs | - |
| `hotfix/<nome>` | Correções urgentes em produção | - |

---

### Processo de Contribuição

1. **Fork** este repositório
2. **Clone** seu fork: `git clone https://github.com/seu-usuario/GerandoFalcoes.git`
3. **Crie uma branch** para sua feature/fix:
   ```bash
   git checkout -b feature/minha-nova-feature
   ```
4. **Faça suas alterações** seguindo os padrões de código
5. **Commit** com mensagens descritivas (veja padrões abaixo)
6. **Push** para seu fork:
   ```bash
   git push origin feature/minha-nova-feature
   ```
7. **Abra um Pull Request** para `develop` (não `main`) no repositório original

---

### Padrões de Código

**Convenções C#:**
- ✅ `PascalCase` para classes, métodos, propriedades
- ✅ `camelCase` para variáveis locais e parâmetros
- ✅ `_camelCase` para campos privados
- ✅ Usar `var` quando o tipo é óbvio
- ✅ Comentar lógica complexa
- ✅ Evitar métodos com mais de 50 linhas (refatorar em helpers)

**Controllers:**
- Manter controllers enxutos (lógica em services/repositories)
- Retornar `IActionResult` com status HTTP corretos
- Validar inputs com `ModelState`

**Migrations:**
- Nomes descritivos: `dotnet ef migrations add AdicionaCampoLinkedinCandidato`
- Sempre revisar migrations antes de aplicar em produção

---

### Padrões de Commit (Conventional Commits)

Use mensagens padronizadas para facilitar geração de changelogs:

| Prefixo | Uso | Exemplo |
|---------|-----|---------|
| `feat:` | Nova funcionalidade | `feat: adiciona endpoint de listagem de candidatos` |
| `fix:` | Correção de bug | `fix: corrige validação de CPF duplicado` |
| `docs:` | Documentação | `docs: atualiza README com instruções de deploy` |
| `refactor:` | Refatoração sem mudança funcional | `refactor: extrai lógica de validação para service` |
| `test:` | Adição/alteração de testes | `test: adiciona testes unitários para CandidatoRepository` |
| `chore:` | Tarefas de manutenção | `chore: atualiza dependências NuGet` |
| `perf:` | Melhorias de performance | `perf: adiciona índice no campo CPF` |

**Exemplo de boa mensagem:**
```
feat: adiciona filtro de status na listagem de candidatos

- Adiciona query parameter 'status' em GET /api/candidatos
- Implementa filtro no repository com LINQ
- Atualiza documentação Swagger
```

---

📝 Roadmap
✅ Sistema Base (Concluído)

 -[x] Cadastro completo de candidatos via web

 -[x] Sistema de autenticação e autorização (RBAC)

 -[x] Gestão de ONGs parceiras (CRUD completo)

 -[x] Distribuição automática de candidatos para ONGs

 -[x] Controle de status da candidatura

 -[x] Validação anti-duplicidade por CPF

 -[x] Dashboard com KPIs principais

 -[x] Integração com Asana

🎯 Próximas Funcionalidades

Hub do Candidato/Aluno
 -[ ] Área exclusiva para o candidato gerenciar seu perfil e acompanhar sua jornada em tempo real:

 -[ ] Visualização do perfil completo

 -[ ] Acompanhamento de status da candidatura

 -[ ] Notificações sobre mudanças de status

 -[ ] Histórico de interações (entrevistas, feedbacks)

 -[ ] Calendário de benefícios e eventos

 -[ ] Integração com Power BI

 -[ ] Conexão direta do banco SQL Server com Power BI para análises avançadas:

 -[ ] Relatórios demográficos sobre candidatos

 -[ ] Análise de áreas geográficas atendidas

 -[ ] Funil de conversão (Inscritos → Aprovados)

 -[ ] Dashboard de performance das ONGs parceiras

 -[ ] Métricas de impacto social

App Mobile
Aplicativo focado na jornada diária e engajamento dos alunos:

 -[ ] Acompanhamento do hub de alunos em dispositivo móvel

 -[ ] Sistema de gamificação para incentivar participação

 -[ ] Calendário integrado de benefícios e eventos

 -[ ] Notificações push em tempo real

 -[ ] Sistema de pontos e recompensas

 -[ ] Ranking de engajamento

 -[ ] Acesso offline a materiais do curso
---

## ⚙️ Boas Práticas e Considerações Técnicas

### 🔒 Segurança

> [!WARNING]
> **Chave JWT em Produção**: A chave JWT atual (`minha-chave-secreta-aqui-123456789`) é apenas para desenvolvimento local. **Nunca faça deploy para produção com essa chave!**
> 
> **Recomendações:**
> - Use Azure Key Vault, AWS Secrets Manager ou variáveis de ambiente seguras
> - Gere chaves com no mínimo 256 bits (32 caracteres)
> - Rotacione chaves periodicamente

> [!CAUTION]
> **CORS em Produção**: A configuração atual usa `AllowAnyOrigin()`, o que aceita requisições de **qualquer domínio**. Isso é um risco de segurança em produção!
> 
> **Correção obrigatória antes de deploy:**
> ```csharp
> builder.Services.AddCors(opt =>
> {
>     opt.AddPolicy("AllowFrontend", builder =>
>     {
>         builder.WithOrigins("https://seu-dominio.com", "https://app.seu-dominio.com")
>                .AllowAnyHeader()
>                .AllowAnyMethod();
>     });
> });
> ```

---

### 🗄️ Banco de Dados

> [!IMPORTANT]
> **Migrations em Produção:**
> - Sempre revise migrations antes de aplicar (`dotnet ef migrations script`)
> - Teste migrations em ambiente de staging primeiro
> - Faça backup do banco antes de aplicar migrations em produção
> - Use transações para rollback em caso de erro

**Connection Strings:**
- ❌ **Nunca comitar** connection strings com senhas reais no Git
- ✅ Use **User Secrets** em desenvolvimento: `dotnet user-secrets set "ConnectionStrings:DefaultConnection" "..."`
- ✅ Use **variáveis de ambiente** em produção

**Índices Recomendados:**
```sql
CREATE INDEX IX_Candidatos_CPF ON Candidatos(CPF);
CREATE INDEX IX_Candidatos_Status ON Candidatos(Status);
CREATE INDEX IX_Candidatos_DataCadastro ON Candidatos(DataCadastro);
```

---

### 🧪 Testes

**Governança de Qualidade:**
- Manter coverage de código acima de 70%
- Testes unitários para repositories e services
- Testes de integração para controllers
- Testes de carga antes de releases (usando k6 ou Artillery)

---

### 📊 Logging e Monitoramento

> [!TIP]
> **Logging Estruturado**: Substitua logs padrão por **Serilog** para structured logging:
> ```bash
> dotnet add package Serilog.AspNetCore
> dotnet add package Serilog.Sinks.File
> ```
> 
> Benefícios: análise de logs mais eficiente, integração com ELK Stack, troubleshooting facilitado.

**Métricas a monitorar:**
- Response time de endpoints
- Taxa de erro (4xx, 5xx)
- Uso de CPU/Memória
- Conexões de banco de dados ativas

---

### 🚀 Performance

**Boas Práticas:**
- ✅ Usar `AsNoTracking()` em queries read-only
- ✅ Implementar paginação em listagens (`Skip` + `Take`)
- ✅ Evitar lazy loading (preferir eager loading com `Include()`)
- ✅ Cachear dados estáticos (Redis ou In-Memory Cache)

---

### 📦 Deployment

**Checklist Pré-Deploy:**
- [ ] Atualizar chaves JWT
- [ ] Configurar CORS restritivo
- [ ] Habilitar HTTPS obrigatório
- [ ] Configurar connection string via variáveis de ambiente
- [ ] Aplicar migrations em staging
- [ ] Executar suite de testes
- [ ] Configurar logs centralizados
- [ ] Configurar monitoramento (Application Insights / New Relic)

---

## 📄 Licença

Este projeto atualmente **não possui licença formal definida**. Para uso e distribuição, recomenda-se:

**Para Open Source:**
- [**MIT License**](https://opensource.org/licenses/MIT) - Licença permissiva que permite uso comercial, modificação e distribuição

**Para Uso Proprietário:**
- **Licença Proprietária** - Uso exclusivo pela organização Gerando Falcões com restrições de distribuição

> [!NOTE]
> **Ação necessária**: Adicione um arquivo `LICENSE` na raiz do repositório após definir a licença apropriada.

---

## 🙏 Agradecimentos

Este projeto é desenvolvido com o apoio da organização **[Gerando Falcões](https://gerandofalcoes.com/)**, que transforma vidas através de educação, tecnologia e oportunidades.

---

<div align="center">

### 🦅 Transformando vidas através da tecnologia

**Desenvolvido com ❤️ para impacto social**

[Reportar Bug](../../issues) • [Solicitar Feature](../../issues) • [Documentação Completa](../../wiki)

</div>
