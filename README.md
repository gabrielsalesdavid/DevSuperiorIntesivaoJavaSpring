# 📚 DevSuperior - Intensivão Java Spring

Projeto educacional do curso **Intensivão Java Spring** da **DevSuperior**, com documentação completa de fundamentos e conceitos avançados de Java.

---

## 📋 Tabela de Conteúdos

- [Visão Geral](#visão-geral)
- [Status do Repositório](#status-do-repositório)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Documentações Criadas](#documentações-criadas)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Como Usar](#como-usar)

---

## 🎯 Visão Geral

Este repositório contém:

- **Código-fonte**: Aplicação Spring Boot para gerenciamento de lista de games
- **Documentação educacional**: Guias completos sobre fundamentos e conceitos avançados de Java
- **Exemplos práticos**: Implementações de padrões de design e boas práticas

### Objetivo Principal

Fornecer uma base sólida no desenvolvimento Java com Spring Boot, incluindo:
- Conceitos fundamentais de Java
- Princípios SOLID e Design Patterns
- Práticas recomendadas de desenvolvimento
- Implementação de API RESTful

---

## 📊 Status do Repositório

### Informações do Git

```
Branch Atual: master
Status: Sincronizado com origin/master
Arquivo: Sem mudanças não commitadas ✅
```

### Últimos Commits

| Commit | Mensagem | Branch |
|--------|----------|--------|
| 25d614d | Add anotation Lombok and new Class | HEAD -> master, origin/master |
| 17efc5a | Add comment and ajust | - |
| 10fcbeb | move gameList | - |
| f726bad | Config cors | - |
| 712e4d5 | Homolog | - |

### Arquivos Não Rastreados

- `Docs/` - Nova pasta com documentações criadas

---

## 📁 Estrutura do Projeto

```
DevSuperiorIntesivaoJavaSpring/
├── src/
│   ├── main/
│   │   ├── java/com/devsuperior/dslist/
│   │   │   ├── DslistApplication.java
│   │   │   ├── config/
│   │   │   │   └── WebConfig.java
│   │   │   ├── controllers/
│   │   │   │   ├── GameController.java
│   │   │   │   └── GameListController.java
│   │   │   ├── dto/
│   │   │   │   ├── GameDTO.java
│   │   │   │   ├── GameListDTO.java
│   │   │   │   ├── GameMinDTO.java
│   │   │   │   └── ReplacementDTO.java
│   │   │   ├── entities/
│   │   │   │   ├── Belonging.java
│   │   │   │   ├── BelongingPK.java
│   │   │   │   ├── Game.java
│   │   │   │   └── GameList.java
│   │   │   ├── projections/
│   │   │   │   └── GameMinProjection.java
│   │   │   ├── repositories/
│   │   │   │   ├── GameListRepository.java
│   │   │   │   └── GameRepository.java
│   │   │   └── services/
│   │   │       ├── GameListService.java
│   │   │       └── GameService.java
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── application-dev.properties
│   │       ├── application-prod.properties
│   │       ├── application-test.properties
│   │       └── import.sql
│   └── test/
│       └── java/com/devsuperior/dslist/
│           └── DslistApplicationTests.java
├── Docs/
│   ├── Fundamentos/
│   │   └── JAVA_FUNDAMENTOS.md
│   └── Conceitos/
│       └── JAVA_CONCEITOS.md
├── Fundamentos/
├── Conceitos/
├── pom.xml
├── mvnw
├── mvnw.cmd
├── system.properties
└── README.md (este arquivo)
```

---

## 📚 Documentações Criadas

### 1. **Fundamentos de Java** 📖
**Arquivo:** `Docs/Fundamentos/JAVA_FUNDAMENTOS.md`

Documentação completa cobrindo os fundamentos essenciais de Java:

#### Conteúdo:
- ✅ Tipos de dados e classes wrapper
- ✅ Variáveis e constantes
- ✅ Operadores (aritméticos, lógicos, relacionais)
- ✅ Estruturas de controle (if-else, switch, loops)
- ✅ Arrays e manipulação de strings
- ✅ Conceitos de Orientação a Objetos
  - Classes e objetos
  - Encapsulamento
  - Herança
  - Polimorfismo
  - Interfaces
  - Classes abstratas
- ✅ Collections (List, Set, Map)
- ✅ Tratamento de exceções
- ✅ Lambdas (Java 8+)
- ✅ Streams

**Público-alvo:** Iniciantes em Java e programadores que desejam revisar conceitos fundamentais.

---

### 2. **Conceitos Avançados de Java** 🚀
**Arquivo:** `Docs/Conceitos/JAVA_CONCEITOS.md`

Documentação detalhada sobre conceitos avançados e boas práticas:

#### Conteúdo:
- ✅ Princípios SOLID
  - Single Responsibility Principle (SRP)
  - Open/Closed Principle (OCP)
  - Liskov Substitution Principle (LSP)
  - Interface Segregation Principle (ISP)
  - Dependency Inversion Principle (DIP)
  
- ✅ Design Patterns
  - Singleton
  - Factory Method
  - Builder Pattern
  - Decorator Pattern
  - Observer Pattern
  
- ✅ Generics
- ✅ Reflexão (Reflection)
- ✅ Anotações customizadas
- ✅ Concorrência
  - Threads
  - Sincronização
  - ExecutorService
  
- ✅ Programação Funcional
  - Function, Predicate, Consumer, Supplier
  
- ✅ Optional
- ✅ Java Time API (java.time)
- ✅ Maven e gerenciamento de dependências

**Público-alvo:** Desenvolvedores intermediários e avançados que desejam dominar técnicas profissionais de desenvolvimento Java.

---

## 🛠️ Tecnologias Utilizadas

### Backend
- **Java 17** - Linguagem de programação principal
- **Spring Boot 3.x** - Framework para construção de aplicações
- **Spring Data JPA** - Persistência de dados
- **Lombok** - Redução de código boilerplate
- **Maven** - Gerenciamento de dependências

### Banco de Dados
- **H2 Database** - Para desenvolvimento e testes
- **PostgreSQL** - Para produção

### Testes
- **JUnit 5** - Framework de testes unitários

---

## 🚀 Como Usar

### Pré-requisitos

```bash
- Java 17 ou superior
- Maven 3.8 ou superior
- Git
```

### Clonar o Repositório

```bash
git clone https://github.com/gabrielsalesdavid/DevSuperiorIntesivaoJavaSpring.git
cd DevSuperiorIntesivaoJavaSpring
```

### Compilar o Projeto

```bash
mvn clean install
```

### Executar a Aplicação

```bash
# Desenvolvimento (H2 Database)
mvn spring-boot:run

# Produção (PostgreSQL)
mvn spring-boot:run -Dspring-boot.run.arguments="--spring.profiles.active=prod"
```

### Executar Testes

```bash
mvn test
```

---

## 📖 Estrutura das Documentações

### Como Ler a Documentação de Fundamentos

1. **Início**: Comece pelos tipos de dados
2. **Progressão**: Siga para estruturas de controle e arrays
3. **OOP**: Aprenda os conceitos de orientação a objetos
4. **Avançado**: Explore Collections, Exceções e Streams

### Como Ler a Documentação de Conceitos

1. **Preparação**: Revise os fundamentos se necessário
2. **SOLID**: Comece pelos princípios de design
3. **Padrões**: Estude os Design Patterns
4. **Avançado**: Aprofunde em Generics, Reflexão e Concorrência

---

## 🎓 Aprendizado com Este Projeto

Através deste repositório, você aprenderá:

### Competências Técnicas
- ✅ Desenvolvimento de APIs RESTful com Spring Boot
- ✅ Arquitetura em camadas (Controller, Service, Repository)
- ✅ Mapeamento relacional (JPA/Hibernate)
- ✅ Validação de dados e tratamento de erros
- ✅ Testes unitários com JUnit
- ✅ Versionamento com Git

### Conceitos de Engenharia de Software
- ✅ SOLID Principles
- ✅ Design Patterns
- ✅ Clean Code
- ✅ Boas práticas de desenvolvimento
- ✅ Padrões de API REST

---

## 📝 Atualizações e Mudanças

### Última Atualização: 13 de Janeiro de 2026

#### Novos Arquivos
```
✨ Docs/Fundamentos/JAVA_FUNDAMENTOS.md
✨ Docs/Conceitos/JAVA_CONCEITOS.md
✨ README.md (este arquivo)
```

#### Status Git
```
Branch: master
Sincronismo: ✅ Atualizado com origin/master
Mudanças pendentes: Docs/ (nova pasta)
```

---

## 🔗 Links Úteis

### Documentação Oficial
- [Java 17 Documentation](https://docs.oracle.com/en/java/javase/17/)
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Maven Documentation](https://maven.apache.org/)

### Recursos de Aprendizado
- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
- [Design Patterns - Refactoring.Guru](https://refactoring.guru/design-patterns)
- [Java Generics Guide](https://docs.oracle.com/javase/tutorial/java/generics/)

---

## 👤 Autor

**Gabriel Sales David**

Repositório: [DevSuperiorIntesivaoJavaSpring](https://github.com/gabrielsalesdavid/DevSuperiorIntesivaoJavaSpring)

---

## 📄 Licença

Este projeto é fornecido como material educacional pelo curso DevSuperior.

---

## 💡 Dicas para Melhor Aprendizado

1. **Leia o código-fonte**: Estude as implementações no diretório `src/main/java`
2. **Experimente**: Crie suas próprias classes e teste os conceitos
3. **Execute os testes**: Veja como o código é testado
4. **Refatore**: Tente aplicar os padrões de design ao seu código
5. **Documente**: Adicione comentários ao seu código explicando o "porquê"

---

**Última atualização:** 13 de janeiro de 2026

