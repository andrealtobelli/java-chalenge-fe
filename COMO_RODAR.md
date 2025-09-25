# 🚀 Como Executar a Aplicação - Sistema de Gestão de Motos

## 📋 Pré-requisitos

Antes de executar a aplicação, certifique-se de ter instalado:

- **Java 17** ou superior
- **Maven 3.6** ou superior
- **MySQL 8.0** ou superior
- **Git** (para clonar o repositório)

## 🛠️ Instalação

### 1. Clone o Repositório
```bash
git clone <URL_DO_REPOSITORIO>
cd universidade_fiap
```

### 2. Configuração do Banco de Dados

#### 2.1. Crie o Banco de Dados
```sql
CREATE DATABASE trackzone_mvc2;
```

#### 2.2. Configure as Credenciais
Edite o arquivo `src/main/resources/application.properties` e ajuste as credenciais do MySQL:

```properties
# Datasource
spring.datasource.url=jdbc:mysql://localhost:3306/trackzone_mvc2?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
spring.datasource.username=SEU_USUARIO_MYSQL
spring.datasource.password=SUA_SENHA_MYSQL
```

## 🚀 Execução

### 1. Compile e Execute a Aplicação
```bash
mvn clean install
mvn spring-boot:run
```

### 2. Acesse a Aplicação
Abra seu navegador e acesse:
```
http://localhost:8080
```

## 👥 Usuários Padrão

A aplicação já vem com usuários pré-cadastrados:

| Email | Senha | Perfil | Descrição |
|-------|-------|--------|-----------|
| admin@fiap.com | admin123 | ADMIN | Acesso total ao sistema |
| gerente@fiap.com | gerente123 | GERENTE | Acesso a relatórios e dashboard |
| operador@fiap.com | operador123 | OPERADOR | Acesso a motos e operações |
| filial1@fiap.com | filial123 | OPERADOR | Filial de exemplo |
| filial2@fiap.com | filial123 | OPERADOR | Filial de exemplo |

## 🔐 Sistema de Autenticação

### Login
- Acesse `http://localhost:8080/login`
- Use qualquer um dos usuários acima
- O sistema redirecionará automaticamente após o login

### Perfis de Acesso

#### 🔴 ADMIN
- ✅ Gerenciar usuários (criar, listar, excluir)
- ✅ Acessar relatórios
- ✅ Acessar dashboard
- ✅ Gerenciar motos e operações

#### 🟡 GERENTE
- ❌ Gerenciar usuários
- ✅ Acessar relatórios
- ✅ Acessar dashboard
- ✅ Gerenciar motos e operações

#### 🟢 OPERADOR
- ❌ Gerenciar usuários
- ❌ Acessar relatórios
- ❌ Acessar dashboard
- ✅ Gerenciar motos e operações

## 📱 Funcionalidades Principais

### 🏠 Página Inicial (`/`)
- Lista todas as motos cadastradas
- Acesso rápido às principais funcionalidades
- Dashboard com estatísticas básicas

### 🏍️ Gestão de Motos (`/motos`)
- **Listar motos**: Visualizar todas as motos cadastradas
- **Cadastrar moto**: Adicionar nova moto ao sistema
- **Editar moto**: Modificar dados de motos existentes
- **Excluir moto**: Remover motos do sistema
- **Status das motos**: Visualizar histórico de status

### ⚙️ Operações (`/operacoes`)
- **Listar operações**: Visualizar todas as operações realizadas
- **Nova operação**: Registrar check-in/check-out de motos
- **Tipos de operação**: Entrega, Coleta, Manutenção, Transferência, Check-in, Check-out

### 📊 Relatórios (`/relatorios`) - *Apenas ADMIN e GERENTE*
- **Relatório de motos**: Lista detalhada de todas as motos
- **Relatório de status**: Histórico de status das motos
- **Relatório de operações**: Operações realizadas no sistema
- **Relatório por período**: Filtros por data

### 📈 Dashboard (`/dashboard`) - *Apenas ADMIN e GERENTE*
- Métricas em tempo real
- Contadores de motos por status
- Estatísticas de operações
- Gráficos e indicadores

### 👥 Gestão de Usuários (`/usuario`) - *Apenas ADMIN*
- **Cadastrar usuário**: Adicionar novos usuários
- **Listar usuários**: Visualizar todos os usuários
- **Excluir usuário**: Remover usuários do sistema

## 🗄️ Estrutura do Banco de Dados

A aplicação utiliza **Flyway** para versionamento do banco. As migrações são executadas automaticamente na inicialização:

- `V1__Create_tables.sql` - Criação das tabelas principais
- `V2__Insert_initial_data.sql` - Dados iniciais
- `V3__Add_dashboard_tables.sql` - Tabelas do dashboard
- `V4__Add_audit_triggers.sql` - Triggers de auditoria
- `V6__Fix_dashboard_table.sql` - Correções do dashboard
- `V7__Fix_enum_values.sql` - Correções dos ENUMs

## 🛡️ Segurança

- **Spring Security** configurado com autenticação por formulário
- **BCrypt** para criptografia de senhas
- **CSRF** habilitado (exceto para endpoints específicos)
- **Proteção de rotas** baseada em perfis de usuário

## 🎨 Interface

- **Thymeleaf** para renderização de templates
- **Bootstrap 5** para interface responsiva
- **Font Awesome** para ícones
- **Fragmentos** para reutilização de código

## 🔧 Configurações Avançadas

### Porta da Aplicação
Para alterar a porta (padrão: 8080), edite `application.properties`:
```properties
server.port=8081
```

### Logs
Para habilitar logs detalhados:
```properties
logging.level.br.com.fiap.universidade_fiap=DEBUG
```

### Banco de Dados
Para usar outro banco de dados, altere a URL no `application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/SEU_BANCO
```

## 🐛 Solução de Problemas

### Erro de Conexão com Banco
- Verifique se o MySQL está rodando
- Confirme as credenciais no `application.properties`
- Certifique-se de que o banco `trackzone_mvc2` existe

### Erro de Porta em Uso
- Altere a porta no `application.properties`
- Ou pare outros serviços na porta 8080

### Erro de Compilação
- Verifique se o Java 17 está instalado
- Execute `mvn clean` antes de `mvn install`

### Dados Não Aparecem
- Verifique se o Flyway executou as migrações
- Confirme se o `DataInitializationService` está funcionando

## 📞 Suporte

Para dúvidas ou problemas:
1. Verifique os logs da aplicação
2. Confirme se todos os pré-requisitos estão instalados
3. Verifique a configuração do banco de dados

## 🎯 Próximos Passos

Após executar a aplicação:
1. Faça login com um usuário ADMIN
2. Explore as funcionalidades disponíveis
3. Cadastre novas motos e usuários
4. Teste os relatórios e dashboard

---

**Desenvolvido com ❤️ usando Spring Boot, Thymeleaf e MySQL**
