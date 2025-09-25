# Sistema de Gestão de Motos - TrackZone

## 📋 Visão Geral
Sistema web desenvolvido em Spring Boot para gestão de motocicletas, incluindo cadastro, controle de status, operações e relatórios.

## 🏗️ Arquitetura do Sistema

### Tecnologias Utilizadas
- **Backend**: Spring Boot 3.5.4
- **Frontend**: Thymeleaf + Bootstrap 5
- **Banco de Dados**: MySQL 8.0
- **Segurança**: Spring Security
- **Build**: Maven
- **Java**: 17

## 📁 Estrutura do Projeto

```
src/main/java/br/com/fiap/universidade_fiap/
├── control/          # Controllers (Camada de Apresentação)
├── model/            # Entidades JPA (Camada de Dados)
├── repository/       # Repositórios JPA (Acesso a Dados)
├── security/         # Configurações de Segurança
├── service/          # Serviços de Negócio
└── UniversidadeFiapApplication.java  # Classe Principal

src/main/resources/
├── templates/        # Templates Thymeleaf
├── static/          # Arquivos Estáticos (CSS, JS)
├── application.properties  # Configurações da Aplicação
└── import.sql       # Dados Iniciais
```

## 🎯 Funcionalidades Principais

### 1. **Autenticação e Autorização**
- Login com email e senha
- Controle de acesso baseado em perfis (ADMIN, USER)
- Senhas criptografadas com BCrypt
- Usuário padrão: `admin@exemplo.com` / `admin1234`

### 2. **Gestão de Usuários**
- Cadastro de novos usuários
- Validação de campos obrigatórios
- Verificação de duplicatas (email, CNPJ)
- Perfis de acesso diferenciados

### 3. **Gestão de Motos**
- Cadastro de motocicletas
- Controle de placa e chassi únicos
- Associação com usuário/filial
- Data de criação automática

### 4. **Controle de Status**
- Atualização de status das motos
- Status disponíveis: PRONTA, ALUGADA, REPARO_SIMPLES, etc.
- Controle de área de localização
- Histórico de alterações

### 5. **Dashboard Dinâmico**
- Contadores em tempo real
- Métricas por status
- Visualização gráfica dos dados
- Atualização automática

### 6. **Relatórios**
- Relatório de motos cadastradas
- Relatório de status
- Relatório de operações
- Exportação de dados

## 📊 Modelos de Dados

### **Usuario**
```java
- id: Long (PK)
- nomeFilial: String
- email: String (único)
- senhaHash: String (BCrypt)
- cnpj: String (único)
- endereco: String
- telefone: String
- perfil: EnumPerfil (ADMIN/USER)
- dataCriacao: LocalDateTime
```

### **Moto**
```java
- id: Long (PK)
- placa: String (única)
- chassi: String (único)
- motor: String
- usuario: Usuario (FK)
- dataCriacao: LocalDateTime
```

### **StatusMoto**
```java
- id: Long (PK)
- moto: Moto (FK)
- status: EnumStatus
- area: String
- dataCriacao: LocalDateTime
```

### **Operacao**
```java
- id: Long (PK)
- moto: Moto (FK)
- tipoOperacao: EnumTipoOperacao
- dataOperacao: LocalDateTime
- observacoes: String
```

## 🎮 Controllers

### **HomeController**
- **Rota**: `/`
- **Função**: Página inicial do sistema
- **Métodos**:
  - `index()`: Exibe dashboard principal com lista de motos

### **LoginController**
- **Rota**: `/login`
- **Função**: Autenticação de usuários
- **Métodos**:
  - `login()`: Exibe formulário de login
  - `loginError()`: Trata erros de login

### **UsuarioController**
- **Rota**: `/usuario/*`
- **Função**: Gestão de usuários
- **Métodos**:
  - `novoUsuario()`: Formulário de cadastro
  - `inserirUsuario()`: Processa cadastro com validações

### **MotoController**
- **Rota**: `/motos/*`
- **Função**: Gestão de motocicletas
- **Métodos**:
  - `listarMotos()`: Lista todas as motos
  - `novoCadastroMoto()`: Formulário de cadastro
  - `salvarMoto()`: Salva nova moto com validações
  - `editarMoto()`: Formulário de edição
  - `atualizarMoto()`: Atualiza moto existente
  - `novoStatusMoto()`: Formulário de status
  - `salvarStatusMoto()`: Salva novo status

### **OperacaoController**
- **Rota**: `/operacoes/*`
- **Função**: Gestão de operações
- **Métodos**:
  - `listarOperacoes()`: Lista operações
  - `novaOperacao()`: Formulário de nova operação
  - `salvarOperacao()`: Salva operação

### **DashboardController**
- **Rota**: `/dashboard`
- **Função**: Dashboard com métricas
- **Métodos**:
  - `dashboard()`: Calcula contadores dinâmicos

### **RelatorioController**
- **Rota**: `/relatorios/*`
- **Função**: Geração de relatórios
- **Métodos**:
  - `relatorios()`: Página de relatórios
  - `relatorioMotos()`: Relatório de motos
  - `relatorioStatus()`: Relatório de status
  - `relatorioOperacoes()`: Relatório de operações

## 🔐 Segurança

### **SegurancaConfig**
- Configuração do Spring Security
- Proteção de rotas por perfil
- CSRF desabilitado para endpoints específicos
- Redirecionamento após login

### **UsuarioDetailsService**
- Implementação do UserDetailsService
- Carregamento de usuários do banco
- Mapeamento de perfis para authorities

## 🗄️ Repositórios

### **UsuarioRepository**
- `findByEmail(String email)`: Busca por email
- `findByCnpj(String cnpj)`: Busca por CNPJ

### **MotoRepository**
- `findByPlaca(String placa)`: Busca por placa
- `findByChassi(String chassi)`: Busca por chassi

### **StatusMotoRepository**
- Operações CRUD para status

### **OperacaoRepository**
- Operações CRUD para operações

## 🎨 Frontend

### **Templates Thymeleaf**
- **home/index.html**: Página inicial
- **home/dashboard.html**: Dashboard com métricas
- **login.html**: Formulário de login
- **usuario/novo.html**: Cadastro de usuário
- **motos/lista.html**: Lista de motos
- **motos/cadastroMotos.html**: Cadastro/edição de motos
- **motos/cadastroStatusMoto.html**: Cadastro de status
- **operacoes/lista.html**: Lista de operações
- **operacoes/cadastro.html**: Cadastro de operações
- **relatorios/lista.html**: Página de relatórios
- **relatorios/motos.html**: Relatório de motos
- **relatorios/status.html**: Relatório de status
- **relatorios/operacoes.html**: Relatório de operações

### **Fragmentos**
- **fragmentos.html**: Componentes reutilizáveis
  - Cabeçalho com CSS/JS
  - Navbar de navegação
  - Formulário de logout
  - Saudações do usuário

## ⚙️ Configurações

### **application.properties**
```properties
# Banco de Dados
spring.datasource.url=jdbc:mysql://localhost:3306/trackzone_mvc2
spring.datasource.username=root
spring.datasource.password=230205

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect

# Flyway desabilitado
spring.flyway.enabled=false
```

### **import.sql**
- Dados iniciais do sistema
- Usuário admin padrão
- Executado automaticamente na inicialização

## 🚀 Como Executar

### **Pré-requisitos**
- Java 17+
- MySQL 8.0+
- Maven 3.6+

### **Passos**
1. **Clone o repositório**
2. **Configure o banco MySQL**
   - Crie o banco `trackzone_mvc2`
   - Execute o script `remove_auditoria.sql` se necessário
3. **Execute a aplicação**
   ```bash
   mvn spring-boot:run
   ```
4. **Acesse**: http://localhost:8080
5. **Login**: admin@exemplo.com / admin1234

## 🔧 Validações Implementadas

### **Usuário**
- Nome da filial obrigatório
- Email válido e único
- Senha mínima 6 caracteres
- CNPJ com 14 dígitos e único
- Perfil obrigatório

### **Moto**
- Placa obrigatória e única
- Chassi obrigatório e único
- Usuário autenticado obrigatório

### **Status**
- Moto obrigatória
- Status obrigatório
- Área obrigatória

## 📈 Dashboard Dinâmico

O dashboard calcula em tempo real:
- **Total de Motos**: Contagem geral
- **Motos Prontas**: Status PRONTA
- **Motos Alugadas**: Status ALUGADA
- **Em Manutenção**: Status de reparo
- **Pendentes**: Status PENDENTE
- **Sem Placa**: Status SEM_PLACA
- **Aguardando Aluguel**: Status AGUARDANDO_ALUGUEL

## 🎯 Navegação

### **Menu Principal**
- **Home**: Dashboard principal
- **Motos**: Gestão de motocicletas
- **Operações**: Controle de operações
- **Relatórios**: Geração de relatórios
- **Dashboard**: Métricas detalhadas

### **Botões de Ação**
- **Nova Moto**: Cadastro de motocicletas
- **Atualizar Status**: Controle de status
- **Nova Operação**: Registro de operações
- **Voltar**: Retorno à página anterior

## 🔍 Logs e Debug

O sistema inclui logs detalhados para:
- Processo de autenticação
- Operações de CRUD
- Validações de dados
- Erros e exceções

## 📝 Notas Importantes

- **Auditoria**: Funcionalidade removida conforme solicitado
- **CSRF**: Desabilitado para endpoints específicos
- **Cache**: Limpeza automática em desenvolvimento
- **Dados**: Persistência garantida com `ddl-auto=update`

## 🐛 Solução de Problemas

### **Erro 500 no Dashboard**
- Verificar se as variáveis estão sendo passadas corretamente
- Limpar cache com `mvn clean compile -U`

### **Erro de Login**
- Verificar se o usuário existe no banco
- Confirmar se a senha está correta

### **Erro de Banco**
- Verificar conexão MySQL
- Confirmar se o banco `trackzone_mvc2` existe
- Executar scripts SQL necessários

---

**Desenvolvido por**: Sistema TrackZone - Gestão de Motocicletas
**Versão**: 1.0.0
**Última Atualização**: Setembro 2025
