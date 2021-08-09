# C# parte 2: Introdução à Orientação a Objetos

## O que é uma classe?

 É uma versão genérica, base, uma descrição das  características (propriedades) e funções (métodos) de algo. Ex: Conta corrente.

### Como criar uma classe?

/code

```
public class ContaCorrente
{
    public string titular;
    public int agencia;
    public int numero;
    public double saldo = 100;  
		// Valor Padrão de saldo
}
```

### Como criar um objeto ou instância de uma classe?

```csharp
NomeDaClasse variavel = new NomeDaClasse();
```

### Como acesar e alterar os campos de um objeto?

```csharp
NomeDaClasse.nomeDoCampo;
```

### Tipo de referência e tipo de valor?

Tipo referência é o endereço na memória (padrão Nullo), tipo valor é o valor propriamente (padrão 0, false, vazio, depende do tipo). 

```csharp
int[] x = new int[];
// X guarda o endereço do array
// Multiplas variaveis podem 
// apontar pro mesmo endereço e alterá-lo

int y = 7;
// y guarda o valor 7
```

### Como definir métodos com parâmetros e retorno?

```csharp
public class ContaCorrente
{
    public string titular;
    public int agencia;
    public int numero;
    public double saldo; // <--- ESSE SALDO

    public bool Sacar(double valor)
    {
        if(this.saldo < valor)
		// O this refere-se ao saldo, 
		// como só tem esse saldo, 
		// o this é facultativo
        {
	            return false;
        }
        else
        {
            this.saldo -= valor; 
		// O this refere-se ao saldo, 
		// como só tem esse saldo, 
		// o this é facultativo
            return true;
        }
    }
}
```

* Usamos o this dentro de um método para acessar um atributo.

### O que é um namespace?

É um container de classes, ou seja, um "escopo" que evita ambiguidade de nomes de classes e métodos. 

### Encapsulamento: Atributos privados

Um atributo privado limita o acesso de outras classes à ele, apenas métodos da própria classe podem chamar essa variável ou método.

### Pra que serve o Get e o Set?

Permitem a modificação ou visualização de propriedades privadas ou protegidas.

```csharp
private double Saldo { get; set; }

public double Saldo { get; private set; }
```

### Pra que serve um construtor?

Obriga uma classe a receber determinados argumentos ou inicializar certo atributo no exato momento em que o objeto é instanciado

### O significa static?

São propriedades da classe (métodos ou atributos), ou seja, comuns a todos os objetos da classe.

```csharp
public ContaCorrente(int agencia, int numero)
{
    Agencia = agencia;
    Numero = numero;

    ContaCorrente.ContasCriadas++;
	   //this.ContasCriadas++;
	   // Objeto.ContasCriadas++;
// Estariam errados, porque é uma propriedade estática
}
```