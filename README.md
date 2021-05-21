**4 Pílares:**

- Abstração: É utilizada para a definição de entidades do mundo real. Sendo onde são criadas as classes. Essas entidades são consideradas tudo que é real, tendo como consideração as suas características e ações, temos que imaginar o que esse objeto irá realizar dentro de nosso sistema. São três pontos que devem ser levados em consideração nessa abstração, com alguns exemplos:
  **Identidade/Entidade** Cachorro
  **Propriedade(atributos/caracteristicas)**: Tamanho/raça/idade etc
  **Métodos**: Latir/correr/morder
  https://www.devmedia.com.br/os-4-pilares-da-programacao-orientada-a-objetos/9264

- Encapsulamento: Conformo o próprio nome segere, a proposta é isolar o máximo possível as nossas classes, de forma a esconder detalhes do funcionamento interno. Visa aumentar a flexibilidade, melhorar a manutenção e aumentar a extensibilidade do Software.

- Herança: Reutilizar código

  - Superclasses e subclasses.
  - Princípio que permite criar uma nova subclasse a partir de uma já existente (superclasse), utilizando a palavra `extends`, ela vai conter atributos e métodos da qual deriva.
  - TypeScript não permite herança múltipla , e isso é bom.
  - O `super` deve ser passado no constructor da subclasse, e ele chama a superclasse, caso a superclasse tenha parametro, o parametro passado no `super` da subclasse é enviado para a superclasse.
  - Caso queria que nenhuma classe possa derivar da sua classe, é só definir seu constructor como private.

- Polimorfismo: Dinamismo para trabalhar chamadas com comportamentos diferentes
  - O principal conceito de duas ou mais classes derivadas de uma mesma **superclasse** responderem a mesma mensagem, cada uma de uma forma diferente. Ocorre quando uma **subclasse** redefine um método existente na superclasse, ou seja, quando temos **métodos sobrescritos (overriding)**
  - Exemplo, temos a **superclasse Mamífero** que tem o método locomoverSe(), e temos as **subclasses Macaco, homem, baleia** todas essas subclasses terão o método locomoverSe(), e cada uma resultará em uma mensagem diferente, (pulando de galho em galho para Macaco), (andando para Homem) e (nadando para Baleia).

**Constructor**

- Construtor é um mecanismo que permite fazer inicializações no objeto assim que ele é instanciado com o new, caso não seja passado é utilizado o construtor padrão(que não tem nenhum parametro). Um bom motivo é colocar no construtor, parametros que queremos que seja obrigatorios. No exemplo do express , dentro do constructor nós iniciamos as rotas/middlewares etc.
  E para encapsular nós utilizamos os _modificadores de acesso_ ( DEFINIDOS ABAIXO )

**Modificadores de acesso** Modificadores de acesso nos permite configurar a visibilidade dos nossos atributos, classes e métodos.

- Public (+):

  - Padrão no Typescript, caso nenhum seja informado. </br>
  - Utilizada de forma restrita, apenas quando desejamos que outras classes "enxerguem" nossa classe, método ou atributo. </br>
  - Torna visível em todo o projeto. </br>
  - Método, sempre que possível não devem ser públicos, mas normalmente são.

- Protected (-):

  - É bem parecido com o _private_, mas se difere porque uma classe que herda de outra pode acessar as variaveis com esse modificador.
  - Utilizado, eventualmente, quando trabalhando com herança.

- Private (#):
  - Utilizada sempre que possível.
  - Torna a visibilidade apenas local (mesmo arquivo, apenas para a classe em si), tornando invisível para outras classes, caso precise, pegar/modificar via get e set.
  - Atributos normalmente são privados.
  - Métodos que implementam rotinas internas (métodos auxiliares (helpers)) devem ser privados.
  - Geralmente no momento que nomear colocamos um underline antes da primeira letra, por convenção.

# Assessores

**Métodos de acesso (GET)** Métodos que tem como única funcionalidade prover acesso aos atributos privados os quais julgamos que devem ser acessados fora do escopo da classe.

- Retornam o tipo de atributo que será provido o acesso.
- Não recebe parâmetro.
- Seu nome é composto pelo prefixo "get" seguido do nome do atributo que o acesso será provido.
- `public get age() : number { return this._age; }`

**Métodos modificadores (SET)** Métodos que tem com única funcionalidade prover modificação aos atributos privados os quais julgamos que podem ser modificados por outras classes.

- Não possuem retorno. (sempre void)
- Recebe por parâmetro o valor a ser inserido no atributo.
- Seu nome é composto pelo prefixo "set" seguido do nome do atributo que iremos possibilitar a modificação
- `public set age(parametro: number) { this._age = parametro; }`
- `classe.age = 35` (esse 35 é o parametro passado no set)

Obs: Crio o atributo privado e depois crio método para acessar e modificar!? Mas porquê?

- Porque nos métodos de acesso podemos controlar como a informação será retornada (no caso dos gets) e que tipo de dado será aceito para a modificação (no caso dos sets) por exemplo colocar alguma validação para aceitar levando em conta o que foi passado no parametro do set... poderia ter um log para quando o atributo ser modificado, ou seja, validações etc

**Vantages da POO**

- Prática de programação
- Segurança
- Reutilização de código
- Fácil manutenção

**Método STATIC** Por definição, um atributo ou método estático é aquele que não requer uma instância para ser utilizado. Isso quer dizer que um método estático, como no seu exemplo, pode ser executado livremente sem a necessidade de instanciação de um objeto.

- Nao é recomendado utilizar em tudo, uma boa ideia é em arquivos de Utilizades UTIL, ou por exemplo aqueles tratamento de erro que eu crio a classe, e depois crio outra subclasse (com seu método static) pra ter um erro mais especifico, e chamar la no throw AppError sem precisar instanciar....
- O padrão Singleton utiliza muito.

**Método ABSTRACT**

- Só pode estar em classe abastrata
- Para poder chamar um método com polimorfismo, a classe onde tem o método deve ser abastrata, porque método abstrato precisa necessiamente de uma classe abastrata
- Método abstrato não tem corpo, a subclasse vai definir o que o métoro irá realiza ali para ela.

**Classe abastrata** É conhecida como classe incompleta porque ela não pode ser instanciada;

- Seus métodos podem ser acessados mesmo sem ela ter sido instanciada, chamamos a classe e o método,`Classe.metodo()`;
- Aparentemente métodos estáticos necessitam que a classe seja abstrata;
- As classes que estenderem dela, poderão ser instanciadas normalmente;
- **_As demais classe que não são abstratas são chamadas de concretas/completas_**
