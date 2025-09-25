# 🚀 Como Usar GitHub Actions - Guia Completo

## 📋 Para seu amigo que vai subir no GitHub Actions

### 🎯 **O que foi configurado:**

✅ **Workflow automático** (`.github/workflows/ci.yml`)
✅ **SQL Server** como banco de dados
✅ **Migrações** compatíveis com SQL Server
✅ **Dependências** SQL Server adicionadas
✅ **Configurações** específicas para CI/CD

### 🚀 **Passos para usar:**

#### 1. **Fazer Push para o GitHub**
```bash
git add .
git commit -m "Configuração GitHub Actions + SQL Server"
git push origin main
```

#### 2. **Verificar no GitHub**
- Acesse: `https://github.com/SEU_USUARIO/SEU_REPOSITORIO`
- Vá na aba **"Actions"**
- Clique no workflow que está rodando
- Acompanhe os logs em tempo real

#### 3. **O que acontece automaticamente:**
- 🐳 **SQL Server 2022** é iniciado em container
- 🗄️ **Banco `trackzone_mvc2`** é criado automaticamente
- 🔄 **Flyway** executa as migrações
- ☕ **Java 17** compila a aplicação
- 🧪 **Testes** são executados
- 📦 **JAR** é gerado e disponibilizado

### 📊 **Verificar se funcionou:**

#### ✅ **Sucesso (verde):**
- Build passou sem erros
- Todos os testes passaram
- JAR foi gerado
- Artifacts disponíveis para download

#### ❌ **Erro (vermelho):**
- Clique no workflow
- Veja os logs detalhados
- Identifique o problema
- Corrija e faça novo push

### 🔍 **Logs importantes para verificar:**

1. **SQL Server Ready** - Banco iniciado
2. **Database Created** - Banco criado
3. **Flyway Migrations** - Migrações executadas
4. **Build Success** - Compilação OK
5. **Tests Passed** - Testes OK

### 🎯 **Usuários para testar:**

| Email | Senha | Perfil |
|-------|-------|--------|
| admin@teste.com | admin1234 | ADMIN |
| gerente@teste.com | admin1234 | GERENTE |
| operador@teste.com | admin1234 | OPERADOR |

### 🐛 **Problemas comuns:**

#### **"SQL Server not ready"**
- Aguarde mais tempo (pode levar até 2 minutos)
- Verifique se o container está rodando

#### **"Database not found"**
- Verifique se o script de criação do banco está correto
- Confirme as credenciais

#### **"Migration failed"**
- Verifique se os scripts SQL estão corretos
- Confirme se não há conflitos de sintaxe

#### **"Build failed"**
- Verifique se todas as dependências estão no pom.xml
- Confirme se o Java 17 está configurado

### 📱 **Como testar localmente:**

Se quiser testar antes de subir:

```bash
# 1. Instalar SQL Server localmente
# 2. Criar banco trackzone_mvc2
# 3. Executar com perfil SQL Server
mvn spring-boot:run -Dspring.profiles.active=sqlserver
```

### 🎉 **Resultado final:**

Após o build bem-sucedido, você terá:
- ✅ Aplicação compilada e testada
- ✅ Banco configurado com dados iniciais
- ✅ JAR pronto para deploy
- ✅ Logs completos de execução
- ✅ Artifacts disponíveis para download

### 📞 **Se der problema:**

1. **Verifique os logs** no GitHub Actions
2. **Confirme se o SQL Server** está rodando
3. **Teste localmente** primeiro
4. **Verifique as dependências** no pom.xml

---

**🎯 Resumo: É só fazer push que funciona automaticamente!**
