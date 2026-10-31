# ListaDeExerc-cio5
**5° lista de exercício da matéria POO. No momento estou sem notebook e sem acesso a um computador por perto, então as questões foram respondidas no README utilizando meu celular**

 1° *A partir do Java 8 passou a ser possível implementar métodos com corpo (default e static) nas interfaces.*

- *Métodos default: Servem para permitir a evolução de interfaces sem quebrar as classes existentes que as implementam, permitindo adicionar novos comportamentos com uma implementação padrão.*
- *Métodos static: Servem para agrupar métodos utilitários relacionados àquela interface diretamente nela, sem a necessidade de criar classes auxiliares separadas.*

 2° *As interfaces ajudam a desacoplar o código porque definem um contrato (o que deve ser feito) separado da implementação concreta (como é feito). Dessa forma, as classes de alto nível dependem de abstrações e não de implementações específicas, facilitando a troca de bibliotecas, manutenção e testes unitários.
   Exemplo prático: Em um sistema de notificações, em vez de acoplar a classe principal diretamente a EmailService, criamos uma interface Notificador. Assim, se no futuro o sistema precisar enviar mensagens via WhatsAppService ou SmsService, basta criar uma nova classe que implementa Notificador sem alterar a lógica principal do sistema.*

3° 
```java
interface AparelhoTelefonico {
    void ligar();
    void atender();
}

interface NavegadorInternet {
    void exibirPagina();
    void adicionarNovaAba();
}

interface ReprodutorMusical {
    void tocar();
    void pausar();
}

class Smartphone implements AparelhoTelefonico, NavegadorInternet, ReprodutorMusical {
    public void ligar() {
        System.out.println("Ligando...");
    }

    public void atender() {
        System.out.println("Atendendo chamada...");
    }

    public void exibirPagina() {
        System.out.println("Exibindo página web...");
    }

    public void adicionarNovaAba() {
        System.com.println("Nova aba adicionada.");
    }

    public void tocar() {
        System.out.println("Reproduzindo música...");
    }

    public void pausar() {
        System.out.println("Música pausada.");
    }
}

public class Principal {
    public static void main(String[] args) {
        Smartphone meuSmartphone = new Smartphone();
        meuSmartphone.ligar();
        meuSmartphone.tocar();
        meuSmartphone.exibirPagina();
        meuSmartphone.pausar();
    }
}
```
4°
```java
interface OperacaoMatematica {
    double executar(double a, double b);
}

public class Principal {
    public static void main(String[] args) {
        OperacaoMatematica soma = (a, b) -> a + b;
        OperacaoMatematica subtracao = (a, b) -> a - b;
        OperacaoMatematica multiplicacao = (a, b) -> a * b;
        OperacaoMatematica divisao = (a, b) -> b != 0 ? a / b : 0;

        System.out.println("Soma: " + soma.executar(10, 5));
        System.out.println("Subtração: " + subtracao.executar(10, 5));
        System.out.println("Multiplicação: " + multiplicacao.executar(10, 5));
        System.out.println("Divisão: " + divisao.executar(10, 5));
    }
}
```
5°
```java
interface Imprimivel {
    void imprimir();
}

interface EnviavelPorEmail {
    void enviar(String email);
}

class RelatorioFinanceiro implements Imprimivel, EnviavelPorEmail {
    public void imprimir() {
        System.out.println("Imprimindo relatório financeiro...");
    }

    public void enviar(String email) {
        System.out.println("Enviando relatório financeiro para: " + email);
    }
}

class Contrato implements Imprimivel {
    public void imprimir() {
        System.out.println("Imprimindo contrato...");
    }
}

public class Principal {
    public static void main(String[] args) {
        java.util.List<Imprimivel> documentos = java.util.List.of(
            new RelatorioFinanceiro(),
            new Contrato()
        );

        for (Imprimivel doc : documentos) {
            doc.imprimir();
            if (doc instanceof EnviavelPorEmail) {
                ((EnviavelPorEmail) doc).enviar("teste@empresa.com");
            }
        }
    }
}
```
  
