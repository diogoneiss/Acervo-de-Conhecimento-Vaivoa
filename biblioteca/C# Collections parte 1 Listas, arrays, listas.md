# C# Collections parte 1: Listas, arrays, listas ligadas, dicionários e conjuntos

### Tópicos (Baseado na Autoavaliação):

- [x]  Manipulação de arrays, descrever sua utilização, suas limitações, ordenar, copiar e clonar *
- [x]  Manipulação de listas, adicionar valores na lista, ordená-la, proteger seus dados com coleções Read-Only *
- [x]  Conjuntos e hashing *
- [x]  Dicionários, manipulação, modificação, adicionar elementos, remover elementos *
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
aulas.sort( (este, outro) => este.Tempo.CompareTo(outro.Tempo) );u
```

### Quando utilizar uma Lista somente leitura (readOnly)?

Ao criamos uma nova classe com uma propriedade lista, podemos "passar por cima" da classe e adicionar um elemento na lista usando o método add (exemplo abaixo), isso pode gerar problemas (exposição indecente). Nesse caso, é necessário limitar o acesso externo à lista e criar um método dentro da classe para adicionar ou remover elementos da lista.

```csharp
Curso csharp = new Curso("C#", "Marcelo");
csharp.Aulas.add( new Aula("Listas", "21");
```

### Como criar uma lista somente leitura (readOnly)?

```csharp
class Curso
{
	private IList<Aula> aulas;
	
	public IList<AUla> Aulas
	{
		get {return new ReadOnlyCollection<Aula>(aulas);
	}
}
// A interface IList é implementada pelo ReadOnlyCollections, é preciso usá-la porque o ReadOnlyCollections
// não retorna uma List, ele retorna uma IList 
```

### Quais as características dos HashSets ou Sets (conjuntos)?

Os sets (ISet<T>) não permitem duplicatas (se você tentar adicionar uma duplicata, ele simplesmente ignora) e os elementos não são armazenados em uma ordem específica (então, você não pode acessar o elemento da posição 4 porque, basicamente, pode ser qualquer elemento). Além disso, os sets costumam ter uma performance melhor que a List e consumir mais memória também.

### O que é uma tabela de dispersão?

É como os valores adicionados no Hash são organizados, um código para cada grupo de elementos do Hash. Esse grupo pode conter 0, 1 ou mais elementos (elementos iguais, serão obrigatoriamente do mesmo grupo), quanto menos elementos ele conter em cada grupo mais eficiente é o hash.

### Como implementar o Equals quando a minha classe possui um HashSet?

A implementação do Equals em si não muda. A diferença é que você precisa implementar o GetHashCode para que a dispersão de elementos seja melhor e assim o seu código performe melhor.

```csharp
public override int GetHashCode()
{
	return this.nome.GetHashCode();
}
```

### Existe alguma classe que intermediária entre a List e o HashSet?

Sim, o SortedSet. Ele implementa um HashSet e ao mesmo tempo mantém uma ordenação crescente dos elementos.

### Quais as características de um dicionário?

Ele associa uma chave (única) a um valor (provavelmente único também, mas poderia não ser). Ao invés de fazer Array[índice], com o IDictionary a gente faz Dicionário[chave] pra ele retornar o valor armazenado na "posição" chave. Você pode sobrescrever um valor reusando o Dicionario[chave] = novoValor.

### Como declarar um dicionário?

```csharp
private IDictionary<int, Aluno> dicALunos = new IDictionary<int, Aluno>();
//                 <Chave, valor>

internal BuscaMatriculado (int numeroMatricula>
{
Aluno aluno = null;
return this.dicAlunos.TryGetValue(numeroMatricula, out aluno);
return aluno;                                   // . Sobrescreve o valor contido em aluno 
}
```

### O que é uma Linked List (Lista ligada)?

É uma lista que não fica armazenada sequencialmente na memória, ao invés disso ela conecta os elementos usando ponteiros. É a coleção mais apropriada para a adição e remoção rápida de elementos ordenados.

### Eu posso criar um array de var e na última posição eu fazer uma referência para a primeira? #ListaCircularExiste?

### Como declarar uma Linked List?

```csharp
LinkedList<string> dias = new LinkedList<string>;

// Como adicionar o primeiro nó
var d4 = dias.AddFirst("Quarta");

// Como adicionar o último nó
var d5 = dias.AddFirst("Quinta");

// Como adicionar antes de um nó
var d2 = dias.AddBefore(d4, "Segunda");

// Como adicionar depois de um nó
var d3 = dias.AddAfter(d2, "Terça");
```

### Como "viajar" entre os nós de uma Linked List?

Para acessar o próximo nó, basta utilizar o método next

```csharp
node3.Next()
// retorna o node 4
```

### Pra que serve um Stack?

O stack segue a lógica de Last in, first out (o último a chegar é o primeiro a sair). É um tipo útil para implementarmos um navegador, aplicação na qual eu preciso ir para um próximo elemento da coleção mas não posso esquecer qual era o elemento anterior. É basicamente uma lista na qual eu posso viajar para o anterior ou para o próximo elemento. (Eu sinceramente, não vi diferença de um stack para uma lista com um ponteiro ;-;)