# C# parte 5: Bibliotecas DLLs, documentação e usando o NuGet

### Como criar uma biblioteca?

Solução (botão direito) → adicionar → Biblioteca de classes 

No projeto (botão direito)  → Adicionar referência → Check na biblioteca criada

### Biblioteca de classes Vs. Aplicativo de console

A biblioteca de classes é onde eu guardo clases (avá) e métodos, é mais um espaço de armazenamento pra evitar duplicatas.

O aplicativo de console é onde eu executo a minha aplicação.

### O que o modificador de acesso internal faz?

Faz uma classe ser exclusiva de um determinado projeto

### O que o modificador de acesso internal protected faz?

Faz com que um método seja exclusivo do projeto e das classes derivadas (ou da própria classe)

### Como adicionar uma descrição a uma biblioteca?

Basta adicionar o /// logo acima da declaração da classe ou método e adicionar o que você quiser. Caso você queira que a descrição seja acessível à outros projetos tem que configurar a criação de um arquivo .xml

```csharp
// Exemplo

///<summary>
///Cria uma instância de ContaCorrente com os argumentos utilizados.
/// <summary>
///<param name="agencia">Representa o valor da proprieddae <see cref="NumeroAgencia" /> e deve possuir um valor maior que zero.</param>
///<param name="numero">Representa o valor da proprieddae <see cref="NumeroDaConta"/> e deve possuir um valor maior que zero.</param>

// Declaração da classe ou método
```

### O que é o NuGet?

É um gerenciador de pacotes (bibliotecas) do .NET, usado para criar e compartilhar bibliotecas públicas ou privadas (entre indivíduos de uma mesma empresa ou organização).