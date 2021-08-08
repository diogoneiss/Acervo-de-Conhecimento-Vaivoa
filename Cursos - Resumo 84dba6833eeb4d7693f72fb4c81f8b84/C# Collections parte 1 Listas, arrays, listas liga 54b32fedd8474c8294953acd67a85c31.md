# C# Collections parte 1: Listas, arrays, listas ligadas, dicionários e conjuntos

### Tópicos (Baseado na Autoavaliação):

- [x]  Manipulação de arrays, descrever sua utilização, suas limitações, ordenar, copiar e clonar *
- [ ]  Manipulação de listas, adicionar valores na lista, ordená-la, proteger seus dados com coleções Read-Only *
- [ ]  Conjuntos e hashing *
- [ ]  Dicionários, manipulação, modificação, adicionar elementos, remover elementos *
- [ ]  Descrever as diferenças e manipular listas ligadas, pilhas e filas *

### Quais as características de um array?

Array é uma coleção de tamanho fixo, de um único tipo (ou classe), não da pra printar o array  bonitinho (igual em python, por exemplo) se você quer acessar um array precisa printar elemento por elemento.

### Como declarar um array?

```csharp
T[] aulas = new T[3];  // Declarando um array de um tipo T

string[] aulas = string[]
{
	"AAA",
	"BBB",
	"CCC"
} 

aulas[0] = "1234"; // Sobrescreve o valor da posição 0;
```

## Da pra criar um array de tipo genérico??

### Como mudar um valor armazenado no array?

É só acessar a posição e sobrescrever o valor.

```csharp
aula1 = "AAA";
aula2 = "BBB";
string[] aulas = new string[] {aula1, aula2};

aula1 = "Não funciona fazer isso" // O array aulas armazena o valor contido em aula1 e não uma referência

aulas[0] = "Isso funciona!"; // Sobrescreve o valor da posição 0;
```

### Quais os principais métodos de um array?

Array.Length → Retorna o tamanho do array.

Array.Reverse → Reverte o array in place (não retorna um array novo).

Array.Resize →  Redimensionar o array (Criando um array internamento).

```csharp
Array.Resize(ref nomeDoMeuArray, novoTamanho);
// Diminuir elimina os últimos elementos
// Aumentar coloca null nas novas posições
```

Array.Sort → Ordena o array in place.

Array.Copy → Copia um array a partir de uma posiçao específica até outra posição específica

Array.Clone → Clona o array todo

```csharp
string[] clone = aulas.Clone() as string[];
			    // . Serve para converter o objeto devolvido por
			    // . aulas.Clone em um array de string, caso a conversão
			    // . falhe ele retorna um null
```

Array.Clear → Sobrescreve o valor armazenado com um null

### O que é uma lista?

Lista é um array dinâmico. Eu posso aumentar  ou diminuir o tamanho da lista sem problemas.

```csharp
Lista.Add(X) // Adiciona o elemento X na última posiçao
Lista.Remove(X) // Remove a primeira ocorrência do elemento X
```

### Como declarar uma lista?

```csharp
List<char> letras = new List<char>();

List<string> aulas = new List<string>
{
	"Aula1",
	"Aula2",
	"Aula3"
};
```

### Quais os principais métodos de uma Lista?

List.ForEach → Executa um código para cada elemento da lista usando action

```csharp
aulas.ForEach(X => { Console.WriteLine(X) });
// Cada elemento chama X e eu to printando X
```

List.First() → Retorna o primeiro elemento da lista

List.Last() → Retorna o último elemento da lista

List.FirstOrDefault() → Retorna o primeiro elemento e se não existir retorna um valor default

List.RemoveAt → Remove um elemente de uma posição específica

List.Sort → Ordena a lista in place

List.GetRange(start, stop) → retorna uma nova lista de strart até stop

List.RemoveRange(start, stop) → remove elementos in place do intervalo especificado

### Como clonar uma lista?

É só instanciar uma nova lista (um objeto)  da lista antiga

```csharp
List<string> clone = new List<string>(listaAntiga);
```

### O que a expressão lambda ( ⇒ ) implementa?

Ela implementa uma função anônima (que eu não sei explicar o que é exatamente, mas me lembra bastante o esquema de List Compreenshion do python)

### Como printar objetos contidos em uma lista?

Você pode acessar propriedade por propriedade ou fazer override do metodo ToString (um método virtual da classe Object)

```csharp
Console.WriteLine(Aulas[0].Titulo);

public override void ToString()
{
	return Aulas.Titulo;
}

Console.WriteLine(Aulas[0]);
```

### Como comparar objetos contidos em uma lista?

Implemente a interface IComparable e o membro CompareTo

```csharp
public int CompareTo(object obj)
{
Aula that = obj as Aula;
return this.titulo.CompareTo(that.titulo);

// O que ele faz é comparar a propriedade título do objeto que está chamando o CompareTo
// com a propriedade título do objeto sendo passado no argumento.
// como ambas propriedades precisam obrigatoriamente ser do mesmo tipo (estão sendo armazenadas
// na mesma propriedade do mesma classe) eu posso compará-los usando o método CompareTo.
}
```

### Exemplo de comparação de objetos usando sort

```csharp
aulas.sort( (este, outro) => este.Tempo.CompareTo(outro.Tempo) );
```

### Como funciona uma Lista somente leitura (readOnly)?