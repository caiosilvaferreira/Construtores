# Construtores

Metodo construtor: ex1:

```csharp
struct Product
{
public Product(int id, string title, float price)
	{
		Id = id;
		Title = title;
		Price = price;
	}
}
```

```csharp
var product = new Product(1, "Mouse Gamer", 128.75f);// aqui os valores de cada variavel
Console.WriteLine(product.Id);
Console.WriteLine(product.Title);
Console.WriteLine(product.Price);
Console.WriteLine(product.PriceInDolar(5.70f));
/* nessa parte ele faz a instanciacao da classe e imprimi os valores na tela*/
```

```csharp
using System;
using System.Globalization;

class meuprimeiroprojeto {
    static void Main(String[] args) {

        Product mouse = new Product(1, "mouse gamer",299.99);//atribuicao de valores

        Console.WriteLine(mouse.Id);  //impressao de valores
        Console.WriteLine(mouse.Name);
        Console.WriteLine(mouse.Price.ToString("F2",CultureInfo.InvariantCulture));
    }

    struct Product {

        public Product(int id, string name, double price) {
//parametros ou variaveis sempre com letra minuscula
// metodo construtor sempre tem que especificar as variaveis detro do parenteses 

            Id=id;    
            Name=name;
            Price=price;
        }
//metodos de propriedades sempre com a primeira letra maiuscula 

        public int Id; 
        public string Name;
        public double Price;

        public double PriceInDolar (double dolar) {
//parametros ou variaveis sempre com letra minuscula
            return Price * dolar;
        }
    }
}
```

Sem o construtor, você teria que inicializar as propriedades manualmente, atribuindo valores a elas após a criação do objeto. Por exemplo, suponha que você tenha a seguinte classe `Product` em C#:

```
class Product
{
    public int Id;
    public string Name;
    public double Price;
}

```

Para criar um novo objeto `Product` e inicializar suas propriedades, você teria que fazer algo assim:

```
Product mouse = new Product();
mouse.Id = 1;
mouse.Name = "Mouse Gamer";
mouse.Price = 128.75;

```

Neste caso, você criou um novo objeto `Product` e inicializou suas propriedades manualmente após a criação do objeto. Note que isso pode se tornar tedioso e propenso a erros se houver muitas propriedades a serem inicializadas.

Por isso, é uma boa prática de programação usar o construtor para inicializar as propriedades de uma classe ou estrutura. Isso torna o código mais legível, fácil de manter e menos propenso a erros.

Espero ter ajudado! Qualquer outra dúvida, é só perguntar.

aqui tem um exemplo pratico de um codigo sem o metodo construtor e depois utilizando o metodo construtor.

```csharp
using System;
using System.Globalization;
namespace Course {
class Program {
static void Main(string[] args) {
Produto p = new Produto();
Console.WriteLine("Entre os dados do produto:");
Console.Write("Nome: ");
p.Nome = Console.ReadLine();
Console.Write("Preço: ");
p.Preco = double.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
Console.Write("Quantidade no estoque: ");
p.Quantidade = int.Parse(Console.ReadLine());
Console.WriteLine();
Console.WriteLine("Dados do produto: " + p);
Console.WriteLine();
Console.Write("Digite o número de produtos a ser adicionado ao estoque: ");
int qte = int.Parse(Console.ReadLine());
p.AdicionarProdutos(qte);
Console.WriteLine();
Console.WriteLine("Dados atualizados: " + p);
Console.WriteLine();
Console.Write("Digite o número de produtos a ser removido do estoque: ");
qte = int.Parse(Console.ReadLine());
p.RemoverProdutos(qte);
Console.WriteLine();
Console.WriteLine("Dados atualizados: " + p);
}
}
}

using System.Globalization;
namespace Course {
class Produto {
public string Nome;
public double Preco;
public int Quantidade;
public double ValorTotalEmEstoque() {
return Preco * Quantidade;
}
public void AdicionarProdutos(int quantidade) {
Quantidade += quantidade;
}
public void RemoverProdutos(int quantidade) {
Quantidade -= quantidade;
}
public override string ToString() {
return Nome
+ ", $ "
+ Preco.ToString("F2", CultureInfo.InvariantCulture)
+ ", "
+ Quantidade
+ " unidades, Total: $ "
+ ValorTotalEmEstoque().ToString("F2", CultureInfo.InvariantCulture);
}
}
}
```

agora com metodo construtor

```csharp
using System;
using System.Globalization;
namespace Course {
    class Program {
        static void Main(string[] args) {
           
            

            Console.WriteLine("Entre os dados do produto:");
            Console.Write("Nome: ");
            string Nome = Console.ReadLine();
            Console.Write("Preço: ");
            double Preco = double.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
            Console.Write("Quantidade no estoque: ");
            int Quantidade = int.Parse(Console.ReadLine());

            Produto p = new Produto(Nome,Preco,Quantidade); /* voce instancia ele aqui, depois das variaveis*/

            Console.WriteLine();
            Console.WriteLine("Dados do produto: " + p);
            Console.WriteLine();
            Console.Write("Digite o número de produtos a ser adicionado ao estoque: ");
            int qte = int.Parse(Console.ReadLine());
            p.AdicionarProdutos(qte);
            Console.WriteLine();
            Console.WriteLine("Dados atualizados: " + p);
            Console.WriteLine();
            Console.Write("Digite o número de produtos a ser removido do estoque: ");
            qte = int.Parse(Console.ReadLine());
            p.RemoverProdutos(qte);
            Console.WriteLine();
            Console.WriteLine("Dados atualizados: " + p);
        }
    }
}

using System.Globalization;
namespace Course {
    class Produto {
        public string Nome;
        public double Preco;
        public int Quantidade;

        public Produto(string nome, double preco , int quantidade) {

            Nome = nome;
            Preco = preco;                        /*esse é o metodo construtor*/
            Quantidade = quantidade;

        }

        public double ValorTotalEmEstoque() {
            return Preco * Quantidade;
        }
        public void AdicionarProdutos(int quantidade) {
            Quantidade += quantidade;
        }
        public void RemoverProdutos(int quantidade) {
            Quantidade -= quantidade;
        }
        public override string ToString() {
            return Nome
            + ", $ "
            + Preco.ToString("F2", CultureInfo.InvariantCulture)
            + ", "
            + Quantidade
            + " unidades, Total: $ "
            + ValorTotalEmEstoque().ToString("F2", CultureInfo.InvariantCulture);
        }
    }
}
```
