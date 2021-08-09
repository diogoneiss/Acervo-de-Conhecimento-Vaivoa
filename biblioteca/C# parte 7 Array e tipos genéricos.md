# C# parte 7: Array e tipos genéricos

## Como inicializar um array?

Um array é um objeto, então inicializa do mesmo jeito.

```csharp
int[] array = new int[tamanho];
// ou
string array = new string[] {"aaa", "bbb", "ccc"};
```

### Como deletar um elemento do array?

Eu não posso diminuir (ou aumentar) o tamanho de um array, então a única maneira seria criar um novo array com o tamanho adequado e passar todos os elementos exceto o elemento deletado.

### Como declarar um método com um número de parâmetros dinâmico?

```csharp
public void AdicionarVarios(params ContaCorrente[] itens)
			 // ^ Permite que eu adicione um array de ContaCorrente
			 //   do tamanho que eu quiser
```

### Como declarar parâmetros opcionais e como chamá-los depois?

```csharp
public void metodo(int numero, double opcional=32.2);
metodo(5, opcional:50.2); 
```

### Pra que servem tipos genéricos?

É um jeito de utilizar um mesmo código para diferentes tipos (avá).

### Como declarar uma lista de tipo genérico?

```csharp
// Declaração

		// . O <T> "guarda o lugar" para um tipo, 
		// . a classe Lista é de um tipo genérico
public class Lista<T>
{
    private T[] _itens;

    public void Adicionar(T item) {}
}

// Pra criar a lista é do mesmo jeito
// que você criaria um objeto
 
Lista<int> listaInt = new Lista<int>;
Lista<char> listaChar = new Lista<char>;
Lista<ContaCorrente> ListaCC = new Lista(ContaCorrente);
```