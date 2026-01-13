# Fundamentos de Java

## Introdução

Java é uma linguagem de programação orientada a objetos, independente de plataforma e amplamente utilizada para desenvolvimento de aplicações robustas e escaláveis.

## 1. Tipos de Dados

### Tipos Primitivos

Java possui 8 tipos primitivos:

- **byte**: Inteiro de 8 bits (-128 a 127)
- **short**: Inteiro de 16 bits (-32.768 a 32.767)
- **int**: Inteiro de 32 bits (padrão para números inteiros)
- **long**: Inteiro de 64 bits
- **float**: Ponto flutuante de 32 bits
- **double**: Ponto flutuante de 64 bits (padrão para decimais)
- **boolean**: Verdadeiro (true) ou Falso (false)
- **char**: Um único caractere Unicode

### Classes Wrapper

- Byte, Short, Integer, Long
- Float, Double
- Boolean, Character

## 2. Variáveis e Constantes

```java
// Variáveis
int idade = 25;
String nome = "João";
double salario = 1500.50;

// Constantes (final)
final String CONSTANTE = "Valor imutável";
final int NUMERO = 100;
```

## 3. Operadores

### Operadores Aritméticos
- `+` (adição)
- `-` (subtração)
- `*` (multiplicação)
- `/` (divisão)
- `%` (resto da divisão)

### Operadores Lógicos
- `&&` (E lógico)
- `||` (OU lógico)
- `!` (NÃO lógico)

### Operadores Relacionais
- `==` (igual)
- `!=` (diferente)
- `<` (menor)
- `>` (maior)
- `<=` (menor ou igual)
- `>=` (maior ou igual)

## 4. Estruturas de Controle

### Condicionais

```java
// if-else
if (idade >= 18) {
    System.out.println("Maior de idade");
} else {
    System.out.println("Menor de idade");
}

// switch
switch (diaDaSemana) {
    case 1:
        System.out.println("Segunda");
        break;
    case 2:
        System.out.println("Terça");
        break;
    default:
        System.out.println("Outro dia");
}
```

### Loops

```java
// for
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// for-each
for (String nome : nomes) {
    System.out.println(nome);
}

// while
while (i < 10) {
    System.out.println(i);
    i++;
}

// do-while
do {
    System.out.println(i);
    i++;
} while (i < 10);
```

## 5. Arrays

```java
// Declaração e inicialização
int[] numeros = new int[5];
int[] numeros = {1, 2, 3, 4, 5};
String[] nomes = new String[3];

// Acessando elementos
int primeiro = numeros[0];
numeros[1] = 10;

// Array multidimensional
int[][] matriz = new int[3][3];
```

## 6. Strings

```java
String texto = "Olá, Mundo!";

// Métodos úteis
int tamanho = texto.length();
String maiuscula = texto.toUpperCase();
String minuscula = texto.toLowerCase();
boolean contem = texto.contains("Mundo");
String[] partes = texto.split(",");
String substituido = texto.replace("Mundo", "Java");
```

## 7. Conceitos de Orientação a Objetos

### Classes e Objetos

```java
public class Pessoa {
    // Atributos
    private String nome;
    private int idade;
    
    // Construtor
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
    
    // Métodos
    public void apresentar() {
        System.out.println("Olá, meu nome é " + nome);
    }
    
    // Getters e Setters
    public String getNome() {
        return nome;
    }
    
    public void setNome(String nome) {
        this.nome = nome;
    }
}
```

### Encapsulamento

- **private**: Acessível apenas dentro da classe
- **protected**: Acessível na classe, pacote e subclasses
- **public**: Acessível de qualquer lugar
- **(sem modificador)**: Acessível no pacote

### Herança

```java
public class Veiculo {
    protected String marca;
    
    public void andar() {
        System.out.println("Andando...");
    }
}

public class Carro extends Veiculo {
    @Override
    public void andar() {
        System.out.println("Carro andando...");
    }
}
```

### Polimorfismo

```java
Veiculo v = new Carro();
v.andar(); // Chama o método de Carro
```

### Interfaces

```java
public interface Veiculo {
    void andar();
    void parar();
}

public class Carro implements Veiculo {
    @Override
    public void andar() {
        System.out.println("Carro andando");
    }
    
    @Override
    public void parar() {
        System.out.println("Carro parado");
    }
}
```

### Classes Abstratas

```java
public abstract class Veiculo {
    abstract void andar();
    
    public void buzinar() {
        System.out.println("Bip bip!");
    }
}
```

## 8. Collections

### List

```java
List<String> nomes = new ArrayList<>();
nomes.add("João");
nomes.add("Maria");
nomes.remove(0);
String primeiro = nomes.get(0);
```

### Set

```java
Set<String> emails = new HashSet<>();
emails.add("email@example.com");
boolean contem = emails.contains("email@example.com");
```

### Map

```java
Map<String, Integer> idades = new HashMap<>();
idades.put("João", 25);
idades.put("Maria", 30);
int idade = idades.get("João");
```

## 9. Tratamento de Exceções

```java
try {
    int resultado = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Erro: " + e.getMessage());
} catch (Exception e) {
    System.out.println("Erro geral");
} finally {
    System.out.println("Sempre executado");
}
```

## 10. Lambdas (Java 8+)

```java
// Sintaxe de lambda
(parametros) -> { corpo }

// Exemplos
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);
numeros.forEach(n -> System.out.println(n));

// Filtragem
List<Integer> pares = numeros.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
```

## 11. Streams (Java 8+)

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);

// Map
List<Integer> dobrados = numeros.stream()
    .map(n -> n * 2)
    .collect(Collectors.toList());

// Filter
List<Integer> maiores = numeros.stream()
    .filter(n -> n > 3)
    .collect(Collectors.toList());

// Reduce
int soma = numeros.stream()
    .reduce(0, Integer::sum);
```

## 12. Anotações

```java
@Override // Indica que sobrescreve um método
public String toString() {
    return "Exemplo";
}

@Deprecated // Marca como obsoleto
public void metodoAntigo() {
}

@FunctionalInterface // Interface com um único método abstrato
public interface Operacao {
    int executar(int a, int b);
}
```

## Referências e Recursos

- [Documentação Oficial Java](https://docs.oracle.com/javase/)
- [Java API Documentation](https://docs.oracle.com/en/java/javase/)
