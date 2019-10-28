# Orientação a Objetos

A orientação a objetos é um paradigma de programação que consiste em transformar as necessidades do seu sistema em classes e objetos.

Como isso funciona? Simples, o POO ou Programação Orientada a Objetos é conhecida por 4 pilares fundamentais, sendo eles:

- Abstração
- Encapsulamento
- Herança
- Polimorfismo

## Objetos

Objeto a grosso modo é tudo aquilo do mundo real que o seu sistema precisa para funcionar, bem como as suas características e comportamentos.

Por exemplo, no Instagram você possui o Post que contém Fotos, Vídeos, Descrição, Likes, Comentários e etc.

Então objeto é tudo aquilo na vida real que pode virar código.

### Abstração

Esse é o conceito primoridal e que se bem entendido faz com que os próximos sejam mais fáceis de entender. A Abstração basicamente consiste em abstrair os objetos necessários para o seu sistema e transforma-lo em classes.

#### Classes

Classes são receitas de bolo que possuem as características e comportamentos do objeto que foi abstraído, basicamente a receita de bolo possui uma formula mágica que é:

```csharp
// A pasta onde se encontra àquela classe
namespace Aula
{
    // É assim que você cria uma classe
    // Basicamente você define o seu nível de acesso
    // Coloca a palavra 'class' e depois nomeia a sua classe
    // Por padrão classes tem o seu nome começado com letra maiúscula
    // E se tiver nome composto iniciar todos com letra maiúscula
    // Por exemplo: Classe, NomeDaClasse
    public class Classe
    {
        // Campo
        // Isso é uma característica da Classe
        // Por padrão as características são escritas utilizando o padrão
        // CamelCase, ou seja, começa sempre com a primeira letra em minísculo
        // E se tiver nome composto iniciar todos com letra maiúscula
        // Por exemplo: campo, nomeDoCampo
        // Ao final do comando sempre coloque ';'
        public string campo;

        // Construtor
        // Isso é um construtor, toda vez que alguém criar um objeto da sua classe
        // Esse método é chamado, basicamente podemos definir como um comportamento
        // Padrão de inicialização
        // Você deve apenas definir um modificador de acesso e colocar depois o nome da Classe
        // Quando a classe tem um construtor sem parametros chamamos esse construtor de 'Construtor Default (Padrão)'
        // Você pode ter quantos construtores quiser
        public Classe()
        {
        }

        // Construtor
        // Isso é um construtor com parametro, ou seja, ao iniciar sua classe você pode escolher qual tipo de comportamento
        // Inicial ela vai ter
        // O nome do parametro segue a mesma regra que o de um campo
        // Exemplo: parametro, nomeDoParametro
        // Se você tivesse apenas este construtor, ao chamar essa classe seríamos obrigados a passar como argumento uma string
        public Classe(string campo)
        {
            // Aqui eu fiz uma atribuição de valor ao campo definido no inicio da classe
            // Note que eu usei a palavra 'this' para acessar o campo de dentro da minha classe.
            this.campo = campo;
        }

        // Método
        // Isso é um comportamento que não retorna nada
        public void MetodoSemRetornoESemParametro()
        {
        }

        // Método
        // Isso é um comportamento que não retorna nada mas que recebe um parametro
        // Os parametros tem tipos pré-definidos e possuem um nome
        // O nome do parametro segue a mesma regra que o de um campo
        // Exemplo: parametro, nomeDoParametro
        // Você pode ter mais de um parametro para o seu método, para isso apenas coloque uma ',' após o parametro
        public void MetodoSemRetornoEComParametro(int parametro1, string parametro2)
        {
        }

        // Método
        // Isso é um comportamento que retorna um valor
        public int MetodoComRetornoESemParametro()
        {
            // O 'return' é o comando utilizado para retornar um valor dentro de um método
            return 0;
        }

        // Método
        // Isso é um comportamento que retorna um valor e recebe um parametro
        // Os parametros tem tipos pré-definidos e possuem um nome
        // O nome do parametro segue a mesma regra que o de um campo
        // Exemplo: parametro, nomeDoParametro
        // Você pode ter mais de um parametro para o seu método, para isso apenas coloque uma ',' após o parametro
        public int MetodoComRetornoEComParametro(int parametro1, string parametro2)
        {
            // O 'return' é o comando utilizado para retornar um valor dentro de um método
            return parametro;
        }
    }
}
```

#### Classe vs Objeto

Classe é a receita de bolo de um objeto, Objeto é quando você dá vida à uma classe.

```csharp
namespace Aula
{
    class Program
    {
        static void Main(string[] args)
        {
            // Para criar um objeto novo devemos apenas usar a palavra 'new' e o nome da classe
            // Igual a criação de uma variável
            // Ao utilizar essa forma, chamamos o Construtor Default
            Classe classe1 = new Classe();

            // Ao utilizar essa forma eu uso o construtor que recebe argumentos no construtor
            Classe classe2 = new Classe("");
        }
    }
}
```

### Herança

Esse conceito consiste em tratar as classes como "pai" e "filho" onde a classe "filha" herda todas as características e comportamentos da classe "pai" quando essas são marcadas com o modificador de acesso `public`, `protected`, `internal` e `protected internal`.

Para exemplificar em código seria dessa forma:

```csharp
namespace
{
    // Essa será a classe Pai
    public class Pai
    {
        // Esse campo será herdado pelas classe 'Filho'
        public string nome;

        // Quando você cria um método construtor na classe 'Pai' você automaticamente
        // Obriga ele a ser implementado na classe 'Filho'
        // Para que não seja obrigado a implementação desse construtor crie um construtor padrão
        public Pai()
        {
        }

        public Pai(string nome)
        {
            this.nome = nome;
        }

        // Esse método será herdado pelas classe 'Filho'
        public void Andar()
        {
        }

        // Se você quiser criar um método que será herdado pelas classes 'Filho'
        // E que em alguma dessas classes ele tenha um comportamento diferente da classe pai
        // É só utilizar a palavra virtual antes do tipo de retorno do método
        public virtual void Falar(string fala)
        {
            Console.WriteLine(fala);
        }
    }

    // Para criar uma herança você simplesmente coloca ':' e depois coloca o nome da classe que será o 'pai'
    public class Filho : Pai
    {
        // Basicamente, por seu pai já possuir o campo 'nome', você naturalmente herda ele
        // Não há a necessidade de criar ele novamente na classe

        // Caso você queira implementar um construtor da classe 'Pai' apenas utilize o base() como abaixo:
        // Como a atribuição ao campo já foi feita no construtor do pai você não tem a necessidade de reimplementa-lá
        public Filho(string nome)
            : base(nome)
        {
        }

        // Para sobrescrever um comportamento da classe pai, o método tem que ter na assinatura a palavra 'virtual'
        // Se tiver, você pode sobrescrever utilizando a mesma assinatura só que troque 'virtual' por 'override'
        public override void Falar(string fala)
        {
            if (this.Pensar())
            {
                // Note que quando estou na classe filho, eu uso o 'this' para pegar tudo que pertence apenas a classe 'Filho'
                // Se eu quiser pegar algo que está disponível apenas no 'Pai' use a palavra 'base'
                // Ou seja, quando eu uso o 'this' eu to falando de tudo que eu implementei de novo ou sobrescrevi do meu 'Pai',
                // O base pega exatamente a forma que está implementado no 'Pai'
                base.Falar(fala);
            }

            Console.WriteLine("Eu pensei e não vou falar");
        }

        // Método disponível apenas na classe 'Filho'
        public bool Pensar()
        {
            return true;
        }
    }
}
```

Dentro da Herança pode ser necessário criar classes 'Pai' que apenas abstraem características e comportamentos em comum com vários objetos e por esse motivo é uma classe que não deve ser transformada em objeto nunca, ou seja é uma classe base para as suas 'Filhas'

```csharp
namespace
{
    // Essa será a classe Pai
    // Marque ela com o 'abstract' e automaticamente essa classe nunca poderá ser instaciada, apenas seus filhos o farão
    public abstract class Pai
    {
        // Caso exista um comportamento que você precise implementar mas que não é genérico, cada classe 'Filho'
        // Implementa da forma que necessitar, marque o método como 'abstract' e ele será obrigado a implementar
        // Em todos os 'Filhos'
        public abstract void Andar();
    }

    public class Filho : Pai
    {
        // Para implementar um método abstrato é semelhante à implementar um método virtual, utilize a palavra 'override'
        // E coloque a assinatura do método igual à classe 'Pai'.
        public override void Andar()
        {
        }
    }
}
```

### Encapsulamento

Esse pilar talvez seja o mais simples de todos conceitualmente, basicamente o encapsulamento consiste em isolar uma regra em um ponto único para que você "proteja" sua classe e para que quem esteja à implementado não tenha que escrever suas regras básicas toda vez que a utilizar.

Por exemplo se o seu campo nome não permite que você tenha menos de 2 caracteres e nem mais de 250, você isola a forma como os outros atribuirão valor ao campo 'nome'

```csharp
namespace
{
    public class Classe
    {
        // Para encapsular primeiramente você deve alterar o modificador de acesso para que não sejam todos que possam
        // Utilizar o seu campo diretamente
        private string nome;

        // Crie um método que todos terão acesso e implemente sua regra lá para que assim todos sejam obrigados a usá-lo
        // Para atribuir valor ao campo 'nome'
        public void SetNome(string nome)
        {
            if (nome < 2 || nome > 250)
            {
                Console.WriteLine("Você não pode atribuir o nome pois ele não está correto.");
            }
            else
            {
                this.nome = nome;
            }
        }

        // Crie um método também para retornar os valores atribuidos, pois seu campo agora é privado e só pode ser visualizado
        // Dentro dessa classe.
        public string GetNome()
        {
            return this.nome;
        }

        // Outra abordagem também é utilizando propriedades que seria da mesma forma que a descrita acima
        // Porém sem a necessidade da declaração de métodos, além de facilitar seu uso
        // Note que o padrão de nomenclatura para Propriedades é igual ao de um método ou de uma classe
        public string Nome
        {
            // Isso é a mesma coisa que o método GetNome()
            get
            {
                return this.nome;
            }
            // Isso é a mesma coisa que o método SetNome(string nome)
            // Porém o parâmetro nome dentro do set tem o nome de value.
            set
            {
                if (value < 2 || value > 250)
                {
                    Console.WriteLine("Você não pode atribuir o nome pois ele não está correto.");
                }
                else
                {
                    this.nome = value;
                }
            }
        }

        // Vamos supor que você possui uma propriedade chamada Idade e não tem regras, apenas deixe ela assim:
        public int Idade { get; set; }
    }

    // Para usar tudo isso é simples, apenas faça assim:
    class Program
    {
        static void Main(string[] args)
        {
            Classe classe = new Classe();

            // Caso você prefira utilizar o modelo de métodos faça assim:
            classe.SetNome("Meu Nome");
            string nome = classe.GetNome();

            // Ou por propriedade que é muito mais simples:
            // A propriedade você apenas a utiliza como se fosse um campo
            classe.Nome = "Meu Nome";
            classe.Idade = 10;
        }
    }
}
```

Obs: Vale lembrar que Propriedade em sí não é encapsulamento, no exemplo acima a propriedade `Idade` não possui regra de atribuição ou de retorno, portanto são apenas mascaras para os campos, encapsulamento é quando você de fato esconde alguma regra para "proteger" ou reaproveitar a regra em um lugar único.

### Polimorfismo

O último pilar é o polimorfismo, ou seja, a capacidade de um objeto assumir multiplas formas, por exemplo, vamos supor que você possui uma herança e que você possui um comportamento que você deve implementar, para isso utilizariamos uma classe abstrata com métodos abstratos como vistos no pilar da herança, porém em muitos cenários você ficará com implementações vázias desses métodos pois não são todos os seus filhos que implementam esse comportamento, só algum deles.

No C# existe uma forma fácil e tranquila de resolver isso usando o conceito de interface: usando o exemplo do Pokemon como da ultima aula, veja como fica o código:

```csharp
using System.Collections.Generic;

namespace
{
    // Perceba o uso da classe abstrata pois a classe 'Pessoa' não necessita ser instaciada diretamente:
    public abstract class Pessoa
    {
        public string Nome { get; set; }

        public Genero Genero { get; set; }

        public string AvatarUrl { get; set; }

        // Método que todos os 'Filhos' devem implementar obrigatóriamente
        public abstract string Cumprimentar();
    }

    // Interface que define quem deve possuis os comportamentos e propriedades adequadas para batalha
    public interface ILutador
    {
        void Batalhar(
            Pokemon meuPokemon,
            ILutador lutadorAdversario,
            Pokemon pokemonAdversario);

        List<Pokemon> PokemonsDeBatalha { get; set; }

        List<Pokemon> MeusPokemons { get; set; }
    }

    // O treinador é uma Pessoa mas também um ILutador
    public class Treinador : Pessoa, ILutador
    {
        public List<Pokemon> PokemonsDeBatalha { get; set; }

        public List<Pokemon> MeusPokemons { get; set; }

        public void Batalhar(
            Pokemon meuPokemon,
            ILutador lutadorAdversario,
            Pokemon pokemonAdversario)
        {
            Pessoa p;
            Vilao v = null;

            if (lutadorAdversario is Vilao)
            {
                p = (Vilao)lutadorAdversario;
                v = (Vilao)p;
            }
            else
            {
                p = (Treinador)lutadorAdversario;
            }

            this.Cumprimentar();
            p.Cumprimentar();

            if (true)
            {
                if (v != null)
                {
                    v.PokemonsRoubados.Add(meuPokemon);
                }
            }
        }

        public override string Cumprimentar()
        {
            return "Olá, eu sou um Treinador, bora Batalhar?";
        }
    }

    // O vilão é uma Pessoa mas também um ILutador
    public class Vilao : Pessoa, ILutador
    {
        public List<Pokemon> PokemonsDeBatalha { get; set; }

        public List<Pokemon> MeusPokemons { get; set; }

        public List<Pokemon> PokemonsRoubados { get; set; }

        public void Batalhar(Pokemon meuPokemon, ILutador lutadorAdversario, Pokemon pokemonAdversario)
        {
        }

        public override string Cumprimentar()
        {
            return "Seus Pokemons são bem legais, passa pra cá!";
        }
    }

    // A médica é uma Pessoa e somente isso
    public class Medica : Pessoa
    {
        public Pokemon PokemonAjudante { get; set; }

        public override string Cumprimentar()
        {
            return "Oi!!";
        }
    }

    public enum Genero
    {
        Feminino = 1,
        Masculino = 2
    }
}
```

Note como você possui várias formas de um mesmo objeto para `Treinador` e `Vilao`, pois ambos possuem características em comum, mas a `Medica`, não possui todas as características, portanto nós criamos uma interface e definimos que apenas as classe que possuem aqueles comportamentos devem implementar as interface.