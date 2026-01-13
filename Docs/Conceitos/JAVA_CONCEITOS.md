# Conceitos Avançados de Java

## Introdução

Este documento apresenta conceitos mais avançados de Java, incluindo padrões de design, práticas recomendadas e técnicas para desenvolvimento profissional.

## 1. Princípios SOLID

### S - Single Responsibility Principle (SRP)

Uma classe deve ter apenas uma responsabilidade.

```java
// ❌ Ruim: múltiplas responsabilidades
public class Usuario {
    public void salvar() { }
    public void enviarEmail() { }
    public void gerarRelatorio() { }
}

// ✅ Bom: cada classe tem uma responsabilidade
public class Usuario {
    public void salvar() { }
}

public class UsuarioService {
    public void enviarEmail(Usuario usuario) { }
}

public class RelatorioUsuario {
    public void gerar(Usuario usuario) { }
}
```

### O - Open/Closed Principle (OCP)

Aberto para extensão, fechado para modificação.

```java
// ❌ Ruim
public class Desconto {
    public double calcular(String tipo, double valor) {
        if (tipo.equals("BLACK_FRIDAY")) {
            return valor * 0.5;
        } else if (tipo.equals("NATAL")) {
            return valor * 0.3;
        }
        return valor;
    }
}

// ✅ Bom
public interface EstrategiaDesconto {
    double calcular(double valor);
}

public class DescontoBlackFriday implements EstrategiaDesconto {
    @Override
    public double calcular(double valor) {
        return valor * 0.5;
    }
}

public class DescontoNatal implements EstrategiaDesconto {
    @Override
    public double calcular(double valor) {
        return valor * 0.3;
    }
}
```

### L - Liskov Substitution Principle (LSP)

Subclasses devem ser substituíveis por suas superclasses.

```java
// ❌ Ruim
public class Passaro {
    public void voar() { }
}

public class Pinguim extends Passaro {
    @Override
    public void voar() {
        throw new UnsupportedOperationException("Pinguim não voa");
    }
}

// ✅ Bom
public abstract class Passaro { }

public interface Voador {
    void voar();
}

public class Passaro extends Voador implements Voador {
    @Override
    public void voar() { }
}

public class Pinguim extends Passaro { }
```

### I - Interface Segregation Principle (ISP)

Clientes não devem depender de interfaces que não usam.

```java
// ❌ Ruim
public interface Trabalhador {
    void trabalhar();
    void comer();
    void dormir();
}

public class Robo implements Trabalhador {
    @Override
    public void trabalhar() { }
    
    @Override
    public void comer() {
        // Robô não come!
    }
    
    @Override
    public void dormir() {
        // Robô não dorme!
    }
}

// ✅ Bom
public interface Trabalhador {
    void trabalhar();
}

public interface Humano {
    void comer();
    void dormir();
}

public class Pessoa implements Trabalhador, Humano {
    @Override
    public void trabalhar() { }
    
    @Override
    public void comer() { }
    
    @Override
    public void dormir() { }
}

public class Robo implements Trabalhador {
    @Override
    public void trabalhar() { }
}
```

### D - Dependency Inversion Principle (DIP)

Dependa de abstrações, não de implementações concretas.

```java
// ❌ Ruim
public class UsuarioService {
    private BancoMysql banco = new BancoMysql();
    
    public void salvar(Usuario usuario) {
        banco.salvar(usuario);
    }
}

// ✅ Bom
public interface BancoRepository {
    void salvar(Usuario usuario);
}

public class UsuarioService {
    private BancoRepository banco;
    
    public UsuarioService(BancoRepository banco) {
        this.banco = banco;
    }
    
    public void salvar(Usuario usuario) {
        banco.salvar(usuario);
    }
}
```

## 2. Design Patterns

### Singleton

Garante uma única instância da classe.

```java
public class Banco {
    private static Banco instancia;
    
    private Banco() { }
    
    public static synchronized Banco getInstance() {
        if (instancia == null) {
            instancia = new Banco();
        }
        return instancia;
    }
}

// Ou com Enum (thread-safe)
public enum Banco {
    INSTANCIA;
    
    public void conectar() { }
}
```

### Factory Method

Cria objetos sem especificar suas classes concretas.

```java
public interface Veiculo {
    void andar();
}

public class Carro implements Veiculo {
    @Override
    public void andar() {
        System.out.println("Carro andando");
    }
}

public class Moto implements Veiculo {
    @Override
    public void andar() {
        System.out.println("Moto andando");
    }
}

public class VeiculoFactory {
    public static Veiculo criar(String tipo) {
        switch(tipo) {
            case "CARRO":
                return new Carro();
            case "MOTO":
                return new Moto();
            default:
                throw new IllegalArgumentException("Tipo desconhecido");
        }
    }
}
```

### Builder Pattern

Constrói objetos complexos passo a passo.

```java
public class Usuario {
    private String nome;
    private String email;
    private int idade;
    private String telefone;
    
    public static class Builder {
        private String nome;
        private String email;
        private int idade;
        private String telefone;
        
        public Builder nome(String nome) {
            this.nome = nome;
            return this;
        }
        
        public Builder email(String email) {
            this.email = email;
            return this;
        }
        
        public Builder idade(int idade) {
            this.idade = idade;
            return this;
        }
        
        public Builder telefone(String telefone) {
            this.telefone = telefone;
            return this;
        }
        
        public Usuario build() {
            Usuario usuario = new Usuario();
            usuario.nome = this.nome;
            usuario.email = this.email;
            usuario.idade = this.idade;
            usuario.telefone = this.telefone;
            return usuario;
        }
    }
}

// Uso
Usuario usuario = new Usuario.Builder()
    .nome("João")
    .email("joao@example.com")
    .idade(30)
    .telefone("1234567890")
    .build();
```

### Decorator Pattern

Adiciona responsabilidades dinamicamente.

```java
public interface Componente {
    void operacao();
}

public class ComponenteConcreto implements Componente {
    @Override
    public void operacao() {
        System.out.println("Operação base");
    }
}

public abstract class Decorador implements Componente {
    protected Componente componente;
    
    public Decorador(Componente componente) {
        this.componente = componente;
    }
}

public class DecoradorA extends Decorador {
    public DecoradorA(Componente componente) {
        super(componente);
    }
    
    @Override
    public void operacao() {
        componente.operacao();
        System.out.println("Decoração A");
    }
}

// Uso
Componente componente = new ComponenteConcreto();
componente = new DecoradorA(componente);
componente.operacao();
```

### Observer Pattern

Define relacionamento um-para-muitos entre objetos.

```java
public interface Observer {
    void atualizar(String mensagem);
}

public class Observador implements Observer {
    private String nome;
    
    public Observador(String nome) {
        this.nome = nome;
    }
    
    @Override
    public void atualizar(String mensagem) {
        System.out.println(nome + " recebeu: " + mensagem);
    }
}

public class Subject {
    private List<Observer> observadores = new ArrayList<>();
    
    public void registrar(Observer observer) {
        observadores.add(observer);
    }
    
    public void remover(Observer observer) {
        observadores.remove(observer);
    }
    
    public void notificar(String mensagem) {
        for (Observer observer : observadores) {
            observer.atualizar(mensagem);
        }
    }
}
```

## 3. Generics

```java
// Classe genérica
public class Caixa<T> {
    private T conteudo;
    
    public void colocar(T item) {
        this.conteudo = item;
    }
    
    public T pegar() {
        return conteudo;
    }
}

// Uso
Caixa<String> caixaString = new Caixa<>();
caixaString.colocar("Olá");
String valor = caixaString.pegar();

// Método genérico
public static <T> void imprimir(T[] array) {
    for (T item : array) {
        System.out.println(item);
    }
}

// Bounded Type Parameter
public static <T extends Number> double somar(T[] numeros) {
    double soma = 0;
    for (T numero : numeros) {
        soma += numero.doubleValue();
    }
    return soma;
}

// Wildcard
public void processar(List<?> lista) { }
public void processar(List<? extends Number> lista) { }
public void processar(List<? super Integer> lista) { }
```

## 4. Reflexão (Reflection)

```java
// Obter classe
Class<?> classe = Usuario.class;
Class<?> classe = Class.forName("com.example.Usuario");

// Obter construtores
Constructor<?>[] construtores = classe.getDeclaredConstructors();

// Obter métodos
Method[] metodos = classe.getDeclaredMethods();

// Obter campos
Field[] campos = classe.getDeclaredFields();

// Invocar método dinamicamente
Method metodo = classe.getMethod("getNome");
Object resultado = metodo.invoke(usuario);

// Criar instância
Constructor<?> construtor = classe.getDeclaredConstructor(String.class);
Object instancia = construtor.newInstance("João");
```

## 5. Anotações Customizadas

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Teste {
    String descricao() default "";
    int timeout() default 5000;
}

public class MinhaClasse {
    @Teste(descricao = "Teste básico")
    public void meuTeste() { }
}
```

## 6. Concorrência

### Threads

```java
// Criando thread
public class MeuRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Executando em thread");
    }
}

Thread thread = new Thread(new MeuRunnable());
thread.start();

// Ou com Lambda
Thread thread = new Thread(() -> {
    System.out.println("Executando em thread");
});
thread.start();
```

### Sincronização

```java
public class Contador {
    private int valor = 0;
    
    public synchronized void incrementar() {
        valor++;
    }
    
    public synchronized int obter() {
        return valor;
    }
}

// Ou com Lock
import java.util.concurrent.locks.*;

public class Contador {
    private int valor = 0;
    private Lock lock = new ReentrantLock();
    
    public void incrementar() {
        lock.lock();
        try {
            valor++;
        } finally {
            lock.unlock();
        }
    }
}
```

### ExecutorService

```java
ExecutorService executor = Executors.newFixedThreadPool(5);

for (int i = 0; i < 10; i++) {
    executor.submit(() -> {
        System.out.println("Tarefa executada");
    });
}

executor.shutdown();
executor.awaitTermination(1, TimeUnit.MINUTES);
```

## 7. Functional Programming

```java
// Function
Function<Integer, Integer> dobrar = x -> x * 2;
int resultado = dobrar.apply(5); // 10

// Predicate
Predicate<Integer> ehPositivo = x -> x > 0;
boolean teste = ehPositivo.test(5); // true

// Consumer
Consumer<String> imprimir = msg -> System.out.println(msg);
imprimir.accept("Olá");

// Supplier
Supplier<String> mensagem = () -> "Olá do Supplier";
String msg = mensagem.get();
```

## 8. Optional

```java
Optional<String> nome = Optional.of("João");
Optional<String> vazio = Optional.empty();

// Operações
nome.isPresent(); // true
vazio.isPresent(); // false

nome.ifPresent(n -> System.out.println(n));
String valor = nome.orElse("Padrão");
String valor = nome.orElseThrow();

// Transformação
Optional<Integer> tamanho = nome.map(String::length);
```

## 9. Datas e Horas (java.time)

```java
import java.time.*;

// LocalDate
LocalDate hoje = LocalDate.now();
LocalDate data = LocalDate.of(2025, 1, 13);

// LocalTime
LocalTime agora = LocalTime.now();
LocalTime hora = LocalTime.of(14, 30, 0);

// LocalDateTime
LocalDateTime dataHora = LocalDateTime.now();

// ZonedDateTime
ZonedDateTime comFuso = ZonedDateTime.now();

// Period e Duration
Period periodo = Period.between(data1, data2);
Duration duracao = Duration.between(hora1, hora2);

// Formatação
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
String formatado = data.format(formatter);
```

## 10. Maven e Gerenciamento de Dependências

```xml
<!-- pom.xml -->
<project>
    <groupId>com.example</groupId>
    <artifactId>meu-projeto</artifactId>
    <version>1.0.0</version>
    
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>3.0.0</version>
        </dependency>
    </dependencies>
</project>
```

## Referências

- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
- [Design Patterns](https://www.oracle.com/java/technologies/design-patterns.html)
- [Java Generics](https://docs.oracle.com/javase/tutorial/java/generics/)
- [Concorrência em Java](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/concurrent/package-summary.html)
