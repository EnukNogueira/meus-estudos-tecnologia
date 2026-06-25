## Segundo curso java

<br>

Private: código para privar o acesso de uma classe 

<br>

### Por que a Herança é tão "Funcional"?

O grande ganho aqui é o **Reuso** e o **Polimorfismo**. Imagine que você está criando um sistema para uma empresa:

- **Superclasse (Mãe):** `Funcionario/Dono` (contém `nome`, `cpf`, `salário`).
- **Subclasses (Filhas):** `Gerente`, `Diretor`, `Secretaria`.

```
// A classe "mãe" (Superclasse)
public class Funcionario {
    private String nome;
    private double salario;

    public double getBonificacao() {
        return this.salario * 0.1;
    }
}

// A classe "filha" (Subclasse) usando 'extends'
public class Gerente extends Funcionario {
    
    // Sobrescrita de método: alterando a regra original
    @Override
    public double getBonificacao() {
        // 'super' chama o comportamento da classe mãe
        return super.getBonificacao() + 1000; 
    }
}
```

- # **Interface**

### 1\. O Contrato

Pense na interface como um **contrato assinado**. Se a classe `ContaCorrente` diz que `implements Tributavel`, ela é obrigada por lei (pelo compilador) a ter o método `getValorImposto()`. Se não tiver, o código nem compila.

### 2\. Múltiplas Implementações

Diferente da herança (onde você só pode herdar de uma classe pai), uma classe em Java pode implementar **várias interfaces** ao mesmo tempo.

- _Exemplo:_ Uma classe `SeguroDeVida` pode ser `Tributavel` e também `Editavel`.

### 3\. Polimorfismo na Prática

Isso permite que você crie listas genéricas. Imagine um "Calculador de Impostos" que não precisa saber se está lidando com uma conta ou um seguro:

Java

<br>

```
public class CalculadorDeImposto {
    private double totalImposto;

    public void registra(Tributavel t) { // Aceita qualquer coisa que seja Tributavel
        double valor = t.getValorImposto();
        this.totalImposto += valor;
    }
}
```

<br>