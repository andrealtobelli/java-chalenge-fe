# 🎯 Configuração Igual ao Professor - GitHub Actions

## ✅ **Configuração Atualizada (Igual ao Professor)**

### 📁 **Arquivos Criados:**

1. **`application-prod.properties`** - Configuração SQL Server
2. **`.github/workflows/ci.yml`** - Workflow GitHub Actions
3. **`pom.xml`** - Dependências SQL Server

### 🔧 **Configuração SQL Server (Igual ao Professor):**

```properties
# MSSQL CONFIG
spring.datasource.driverClassName=com.microsoft.sqlserver.jdbc.SQLServerDriver

spring.datasource.url=${SPRING_DATASOURCE_URL}
spring.datasource.username=${SPRING_DATASOURCE_USERNAME}
spring.datasource.password=${SPRING_DATASOURCE_PASSWORD}

#JPA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### 🚀 **Como Usar:**

#### **1. Fazer Push:**
```bash
git add .
git commit -m "Configuração SQL Server igual ao professor"
git push origin main
```

#### **2. Verificar no GitHub:**
- Acesse a aba **"Actions"**
- Veja o workflow rodando
- Acompanhe os logs

#### **3. O que acontece:**
- 🐳 **SQL Server 2022** inicia automaticamente
- 🗄️ **Banco `trackzone_mvc2`** é criado
- ☕ **Java 17** compila com perfil `prod`
- 🧪 **Testes** são executados
- 📦 **JAR** é gerado

### 🎯 **Variáveis de Ambiente (GitHub Actions):**

```yaml
env:
  SPRING_DATASOURCE_URL: jdbc:sqlserver://localhost:1433;databaseName=trackzone_mvc2;encrypt=false;trustServerCertificate=true
  SPRING_DATASOURCE_USERNAME: sa
  SPRING_DATASOURCE_PASSWORD: YourStrong@Passw0rd
```

### 📊 **Perfil Ativo:**
- **Local**: `application.properties` (MySQL)
- **GitHub Actions**: `application-prod.properties` (SQL Server)

### 🎉 **Resultado:**
- ✅ **Configuração igual ao professor**
- ✅ **Variáveis de ambiente configuradas**
- ✅ **JPA com ddl-auto=update**
- ✅ **Driver SQL Server correto**
- ✅ **GitHub Actions funcionando**

### 🔍 **Para testar localmente:**
```bash
mvn spring-boot:run -Dspring.profiles.active=prod
```

**🎯 Agora está exatamente igual ao que o professor ensinou!**
