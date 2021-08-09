# C# parte 6: Strings, expressões regulares e a classe Object

### Depois de criada, eu posso alterar uma string?

Nops, strings são imutáveis.

```csharp
// Eu não posso fazer isso, porque a string é imutável
string s = "abcde";
s[0] = "6";

// Por baixo dos panos, 
// eu estou criando uma nova string
// que contém a string velha e a string a ser adicionada
string s = "abcde";
s += " 123456";

s == "abcde 123456";
```

### O que o método String.Substring faz?

Retorna o índice de uma substring em uma string

### O que o método String.IsNullOrEmpty faz?

Checa se uma string é nula ou vazia

### O que é REGEX?

É usado para encontrar um padrão de carácteres dentro de uma string que não possuam um início ou um fim bem definido.

```csharp
// Todos são números de telefone
Me ligue em 7894-4654
Meu número de telefone é 7894-4654
O número 7894-4654 é para contato profissional
```

### Como usar o REGEX?

```csharp
string s = "aaaaaaaaaaa 1234-1234 aaaaaaaaaaaa";
string padrão = "[0-9]{5,4}-?[0-9]{4}";

// [0-9] -> Um número de 0 a 9
// {5,4} -> O valor anterior aparece 5 ou 4 vezes
// -? -> O valor é facultativo (seria o mesmo que {1,0})

Match resultado = Regex.Match(s, padrão);

resutlado == "1234-1234";
```

### O que é a classe Object?

É a classe mãe, da qual todos as outras classes derivam.

### O que o método Object.ToString() faz?

O ToString() retorna uma string (o padrão é o nome da Classe). Mas você pode sobrescrevê-lo (ele é virtual) e trocar a string que representa o objeto ou só mudar mesmo. 

```csharp
class ContaCorrente
{

    public override string ToString()
	{
	return "Executando ToString sobrescrito!";
	}
}

// Agora se eu executar
ContaCorrente cc = new ContaCorrente();
Console.WriteLine(cc);
// O console vai printar
// "Executando ToString sobrescrito!"
```

### O que o método Object.Equals faz?

Ele compara dois objetos. Eu posso sobrescrevê-lo e comparar campo a campo de um objeto (caso eu não esteja usando uma "classe padrão").

```csharp
public override bool Equals(object obj)
{
    Cliente outroCliente = obj as Cliente;

    return
        Nome == outroCliente.Nome &&
        CPF == outroCliente.CPF &&
        Profissao == outroCliente.Profissao;
}
```

### Como fazer casting sem dar erro?

É só usar a palavra reservada *as*

```csharp
Cliente outroCliente = obj as Cliente;
// Se não for possível converter, passa o NULL
```