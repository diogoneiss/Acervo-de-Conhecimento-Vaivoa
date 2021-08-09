# C# parte 4: Entendendo exceções

### O que é CallStack (pilha de chamadas)?

É a ordem em que os métodos são tratados, o main executa o methodA que executa o methodB que executa o methodC. Quando o C termina (último da fila), o B pode terminar e assim sucessivamente.

![C#%20parte%204%20Entendendo%20excec%CC%A7o%CC%83es%20eb3c0ae809e64b9f8a079846fbc82c68/Untitled.png](C#%20parte%204%20Entendendo%20excec%CC%A7o%CC%83es%20eb3c0ae809e64b9f8a079846fbc82c68/Untitled.png)

### Como tratar exceções?

```jsx
try
{
	// Código que pode gerar um erro
}
catch
{
	// Deu erro? Faça isso.
}
finally
{
	// Independente do que aconteça execute esse código
}
```

### Pra que serve o Message e o StackTrace??

Message é uma propriedade das classes "filhas" da classe exception que é incluída quando o ToString (metodo da classe Exception) é retornada. Eu posso sobrescrever o message.  O StackTrace é uma propriedade que guarda o CallStack das chamados (quais métodos foram chamados antes do erro)

### Por que é importante colocar os catchs mais específicos primeiro?

Porque os blocos catchs são executados de cima para baixo (como os blocos if, else if, else).

### O que a função throw faz?

Ele sai do método (tipo o return)

```csharp
  try
  {
          return numero / divisor;
  }
  catch (DivideByZeroException)
  {
          Console.WriteLine("Exceção com numero=" + numero + " e divisor=" + divisor);
          throw;
	  // Nada que eu colocar depois será executado :c
  }
```

### Como usar o ArgumentException e o nameof?

```csharp
if (numeroConta <= 0)
{
        string teste = nameof(numeroAgencia); // vai ser "numeroAgencia"

        throw new ArgumentException("O argumento numero deve ser maior que 0." + teste);
}
```

### Throw vs Throw ex

Usar o *throw ex;* dentro de um catch vai resultar na perda de informações a respeito da exceção original

### O que é uma inner exception?

É a exceção que causou a exceção atual. É utilizada quando eu não quero mostrar a exceção verdadeira. É como se eu desse um throw em uma excessão mais genérica (ou menos sensível).

### O que a interface IDisposable implementa?

Ela permite que eu não cheque por null indiretamente é um açúcar sintático.