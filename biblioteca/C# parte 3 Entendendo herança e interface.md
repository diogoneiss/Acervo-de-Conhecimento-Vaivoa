# C# parte 3: Entendendo herança e interface

### O que são sobrecargas?

São métodos com o mesmo nome mas com parâmetros diferentes.

### O que é Herança?

É quando uma classe herda métodos e propriedades de uma classe base.

```csharp
public class filho : pai
```

### O que é polimorfismo?

Duas classes derivadas de uma mesma classe base, herdam a obrigatoriedade de declarar um método (cada uma aplica o método considerando suas particularidades)

### Modificadores virtual e override

Caso a maioria dos objetos utilizem um método declarado na classe, mas um deles precise utilizar esse método de um jeito diferente eu posso sobrescrevê-lo.

```csharp
public class Funcionario
{
    public virtual double GetBonificacao()
    {
        return 100;
    }
}

public class Diretor : Funcionario
{
    public override double GetBonificacao()
    {
        return 200;
    }
}
```

### Palavra reservada base

Permite que eu me refira a um membro da classe base

```csharp
public override double GetBonificacao()
{
    return Salario + base.GetBonificacao();
	           // Esse GetBonificacao é 
		   // implementado na classe base
}
```

## Modificador protected

A classe atual e as derivadas tem acesso á propriedade (método ou dado)

### Métodos abstratos

Impede a criação de um objeto da classe base, uma vez que não faz sentido eu criar um "funcionário" se eu posso criar um "cargo" que herda as propriedades do funcionário. Métodos abstratos não possuem corpo, só assinatura

## Sobrecarga em construtores

Quando eu herdo classes que obrigam o preenchimento de certos argumentos no momento de criar o objeto eu preciso chamar a classe pai e repassar tais argumentos.

```csharp
public Funcionario(double salario, string cpf)
{
    Salario = salario;
    CPF = cpf;
}

public Diretor(string cpf) : base(5000, cpf)
{
}
```

### Pra que serve interfaces?

A interface é um contrato no qual quem assina se responsabiliza por implementar os métodos "apresentados" na interface (todos os métodos são públicos)

(A INTERFACE NÃO IMPLEMENTE NADA, ELA SÓ DIZ O QUE PRECISA SER IMPLEMENTADO)

```csharp
public abstract class FuncionarioAutenticavel : Funcionario, IAutenticavel
		   // ^ Clase Filha             ^Classe Pai  ^Interface
```

### Classe abstrata e interface

Classes abstratas que herdam uma interface precisam declarar os métodos, mesmo que seja só pra ter a assinatura.