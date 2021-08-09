# C# Parte 9: Entrada e saída (I/O) com streams

### Como lidar com arquivos grandes e maiores que a RAM do Computador?

Não tentar pegar tudo de uma vez, usar o Read para limitar o número de bytes que você pega por vez (caso necessário você pode pegar do 0 - 10, depois do 11 - 20, 21 - 30, 31 - 40....

### O que são Streams?

É o acesso à um determinado recurso sob demanda. Você pode consumir as informações de um .txt através de uma conexão contínua sem se preocupar com o tamanho do arquivo, já que você não precisa ler todo o arquivo de uma vez.

### Como usar o método Read e buffers?

```csharp
public override int Read(byte[] array, int offset, int count);
// byte[] array --> Array temporário (buffer) onde serão armazenados os bytes lidos pelo método
// int offset --> Índice de onde começará a a preencher o array
// int count --> Máximo de índices que ele vai preencher por chamada
```

### Endereço de arquivo absoluto

```csharp
string endereço = "C:/documentos/arquivo.txt"
```

### Endereço de arquivo relativo

```csharp
string endereço = "arquivo.txt"
```

### Unicode e enconding UTF

Unicode é uma lista de que define o códigos de todos os caracteres. Enconding UTF é a tradução de unicode para um determinado "estilo", o padrão é o UTF-8.

### O modificador partial

Permite o uso de duas classes com o mesmo nome no mesmo namespace, seus membros são "somados" na compilação.

### O método Close de um stream

Sempre que abrir um arquivo é necessário fechá-lo depois. 

```csharp
fluxoDoArquivo.Close();
using(var fluxoDoArquivo = new FileStream(enderecoDoArquivo, FileMode.Open)) {}
```

### Como usar o StreamReader

```csharp
namespace ByteBankImportacaoExportacao
{
  partial class Program
  {
      static void Main(string[] args)
      {
          var enderecoDoArquivo = "contas.txt";
          using (var fluxoDeArquivo = new FileStream(enderecoDoArquivo, FileMode.Open))
          {
              var leitor = new StreamReader(fluxoDeArquivo);

              var linha = leitor.ReadLine()
              Console.WriteLine(linha);
          }
          Console.ReadLine();
      }
  }
}
```

### O Read, ReadLine e ReadToEnd

```csharp
StreamReader.Read() -> Retorna a int do primeiro byte
StreamReader.ReadLine() -> Retorna uma linha por vez ("....\n")
StreamReader.ReadToEnd() -> Retorna tudo de uma vez ;-;
```

### A propriedade EndOfStream

Retorna falso quando chega ao fim de uma Stream

### **int.Parse**

Converte uma string em um inteiro.

### **double.Parse**

Converte uma string em um double (preste atenção no separador da vírgula).

### **Como escrever diretamente no Stream?**

```csharp
using (var fluxoDeArquivo = new FileStream(caminhoNovoArquivo, FileMode.Create))
using (var escritor = new StreamWriter(fluxoDeArquivo, Encoding.UTF8))
{
  escritor.Write("456,65465,456.0,Pedro");
}
```

### Diferença entre FileMode.Create e FileMode.CreateNew

FileMode.Create cria ou sobrescreve o arquivo. Já o FileMode.CreateNew cria ou lança uma exceção.

### Como usar o StreamWriter?

```csharp
static void CriarArquivoComWriter();
{
  var caminhoNovoArquivo = "contasExportadas.csv"

  using (var fluxoDeArquivo = new FileStream(caminhoNovoArquivo, FileMode.CreateNew))
  using (var escritor = new StreamWriter(fluxoDeArquivo))
  {
      escritor.Write("456,65465,456.0,Pedro");
}
```

---

### O método Flush

O StreamWriter não fica passando os dados imediatamente para o arquivo, ele acumula para passar tudo de uma vez. O método Flush passa os dados em tempo real (menor performance) mas eu consigo manter os dados mesmo que aplicação quebre.

### BinaryReader e BinaryWriter

Representar texto em binário. O BinaryReader "lê" o código binário usando um enconding para traduzí-lo. Já o BinaryWriter "lê" um "texto normal" e usa o enconding para transformá-lo em binário.

### Como a Console funciona com streams e Console.OpenStandartInput();

Permite que você receba o que o usuário digita na Console.

### Métodos Auxiliares na classe File

Ao invés de usar o Console.OpenStandartinput() você pode usar o maldito Console.ReadLine()... turururu.

Métodos auxiliares: WriteAllText, WriteLine, ReadAllBytes, ReadAllLines