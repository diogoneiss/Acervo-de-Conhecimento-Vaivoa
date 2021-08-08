# C# parte 8: List, lambda, linq

### Como declarar uma Classe List dotNet?

```csharp
List<T> itens = new List<T>(); // T é um tipo genérico
//ou
List<double> itens = new List<double>();
```

### O que é um método de extensão?

É, a grosso modo, um"açúcar sintático" pra quando você precisa passar um objeto como argumento.

```csharp
ListExtensoes.AdicionarVarios(idades, 1,5,6,7,3);
			   // ^ idades é um objeto sendo passado como argumento

// Um jeito mais bonitinho seria
idades.AdicionarVarios(1,5,6,7,3);

// Essencialmente, é o que você está fazendo no primeiro caso
// você só chama a classe ListExtensoes para ter acesso ao método AdicionarVarios
```

### Como criar um método de extensão?

```csharp
public static void ListEstensoes <T>
{                             // . O this meio que puxa o objeto que está chamando
                              // . o método para dentro dos parametros. É como se
                              // . eu dissesse "use o objeto que chama o método,
                              // . como um argumento do próprio método)
   public static void AddVarios (this List<T> listaInt, params T[] itens)
   {
      // faz algo....
   }
}
```

### O que é uma expressão lambda?

### Como utilizar uma expressão lambda?

```csharp
IOrderedEnumerable<ContaCorrente> contasOrdenadas = 
    contas.OrderBy(conta => conta.Numero);

foreach (var conta in contasOrdenadas)
{
        Console.WriteLine($"Conta número {conta.Numero}, ag. {conta.Agencia}");
}
```

### O que é LINQ?

É um namespace ou biblioteca (um container de classes e métodos) que faz ordenação por métodos de extensão.