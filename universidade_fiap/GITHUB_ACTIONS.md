# 🚀 GitHub Actions - Sistema de Gestão de Motos

## 📋 Configuração para GitHub Actions

Este projeto está configurado para rodar automaticamente no GitHub Actions usando SQL Server.

### 🔧 Configurações Incluídas

#### 1. **Workflow CI/CD** (`.github/workflows/ci.yml`)
- ✅ Execução automática em push/PR
- ✅ SQL Server 2022 como serviço
- ✅ Java 17 com Maven
- ✅ Cache de dependências
- ✅ Build e testes automáticos

#### 2. **Configuração SQL Server** (`application-sqlserver.properties`)
- ✅ Driver SQL Server configurado
- ✅ Flyway para migrações
- ✅ Dialeto Hibernate para SQL Server

#### 3. **Dependências Adicionadas**
- ✅ `mssql-jdbc` - Driver SQL Server
- ✅ `flyway-database-sqlserver` - Migrações SQL Server

### 🗄️ Migrações SQL Server

#### **V1__Create_tables_sqlserver.sql**
- Criação das tabelas principais
- Compatível com SQL Server 2022
- Constraints e foreign keys configurados

#### **V2__Insert_initial_data_sqlserver.sql**
- Dados iniciais do sistema
- Usuários padrão para teste
- Motos e operações de exemplo

### 🎯 Como Funciona

1. **Push/PR** → GitHub Actions é acionado
2. **SQL Server** → Container SQL Server 2022 é iniciado
3. **Database** → Banco `trackzone_mvc2` é criado automaticamente
4. **Flyway** → Migrações são executadas
5. **Build** → Aplicação é compilada e testada
6. **Artifacts** → JAR é gerado e disponibilizado

### 👥 Usuários de Teste

| Email | Senha | Perfil | Descrição |
|-------|-------|--------|-----------|
| admin@teste.com | admin1234 | ADMIN | Acesso total |
| gerente@teste.com | admin1234 | GERENTE | Acesso a relatórios |
| operador@teste.com | admin1234 | OPERADOR | Acesso básico |

### 🔍 Verificação do Build

Para verificar se está funcionando:

1. **Acesse** a aba "Actions" no GitHub
2. **Verifique** se o workflow está rodando
3. **Confira** os logs de execução
4. **Baixe** os artifacts gerados

### 🐛 Solução de Problemas

#### **Erro de Conexão SQL Server**
- Verifique se o serviço SQL Server está rodando
- Confirme as credenciais no workflow
- Aguarde o tempo de inicialização (30s)

#### **Erro de Migração**
- Verifique se os scripts SQL estão corretos
- Confirme se o banco foi criado
- Verifique os logs do Flyway

#### **Erro de Build**
- Verifique se todas as dependências estão no pom.xml
- Confirme se o Java 17 está configurado
- Verifique se não há conflitos de versão

### 📊 Status do Build

- ✅ **Compilação**: Java 17 + Maven
- ✅ **Banco**: SQL Server 2022
- ✅ **Migrações**: Flyway automático
- ✅ **Testes**: Execução automática
- ✅ **Build**: JAR gerado
- ✅ **Artifacts**: Disponíveis para download

### 🎉 Resultado

Após o build bem-sucedido, você terá:
- ✅ Aplicação compilada e testada
- ✅ Banco de dados configurado
- ✅ Dados iniciais inseridos
- ✅ JAR pronto para deploy
- ✅ Logs completos de execução

---

**Desenvolvido com ❤️ para GitHub Actions + SQL Server**
