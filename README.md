<a href="https://github.com/IsaacAlves7/hexagonal-architecture"><img src="https://github.com/user-attachments/assets/58aea475-a132-4824-bbc9-68a95e7650d6"></a>

> Versículo chave: "Consagre ao Senhor tudo o que você faz, e os seus planos serão bem-sucedidos." - Provérbios 16:3

# 🛑 Hexagonal architecture (Ports & Adapters)
<img src="https://img.shields.io/badge/Spring_Boot-3.10.7-limegreen?style=flat&logo=Spring&logoColor=white"> <img src="https://img.shields.io/badge/Kotlin-16-indigo?style=flat&logo=Kotlin&logoColor=white">  <img src="https://img.shields.io/badge/.NET-10-indigo?style=flat&logo=.NET&logoColor=white"> <img src="https://img.shields.io/badge/Node.js-16.17.0-339933?style=flat&logo=Node.js&logoColor=white"> <img src="https://img.shields.io/badge/RabbitMQ-16-orange?style=flat&logo=RabbitMQ&logoColor=white"> <img src="https://img.shields.io/badge/PostgreSQL-16.17-blue?style=flat&logo=PostgreSQL&logoColor=white"> <img src="https://img.shields.io/badge/MongoDB-16-lime?style=flat&logo=MongoDB&logoColor=white">

<img src="https://github.com/user-attachments/assets/cf1c6771-55e1-4999-825e-c8d3ace2a1ad" align="right" height="77">

A **arquitetura hexagonal** é um design de software, também conhecida como Arquitetura de **Portas e Adaptadores (Ports and Adapters)**, na qual é uma abordagem de design que promove a separação clara de preocupações e a independência da lógica central da aplicação em relação aos detalhes técnicos e de infraestrutura (camada de negócios e a infraestrutura), como banco de dados, facilitando a manutenção e evolução do sistema. É uma abordagem de design de sistema destinada a desacoplar a lógica de negócios principal de um software de suas interações externas. 

A Arquitetura Hexagonal, também conhecida como Arquitetura de Portas e Adaptadores, isola dependências, tornando mais fácil a criação de testes unitários e de integração mais robustos e confiáveis. 

A imagem representa visualmente essa arquitetura, colocando as **entidades principais** (lógica de negócios) no centro do sistema, protegidas de dependências externas, como bancos de dados, APIs e filas de mensagens. O **núcleo** se comunica com o mundo exterior por meio de **portas** (interfaces), que atuam como limites que definem o que o sistema central espera em relação à entrada e saída.

A arquitetura Hexagonal, também conhecida como Arquitetura de Portas e Adaptadores, foca em isolar a lógica central da aplicação (domínio) de detalhes de implementação externos, propõe separar o núcleo (core) da aplicação (domínio) das interfaces externas (como UI, banco de dados, APIs) através de portas (interfaces) e adaptadores (implementações). 

Ao redor do núcleo estão adaptadores que interagem com componentes externos. Esses adaptadores implementam a funcionalidade exigida pelas portas. Por exemplo, solicitações HTTP ou interações com um banco de dados são tratadas por adaptadores específicos, que convertem os dados em um formato que as entidades principais podem processar. Isso fica evidente na imagem, onde diferentes sistemas externos, como HTTP, SQS (fila de mensagens), DB (banco de dados), API REST e API GRPC, são conectados por meio de camadas que processam solicitações e respostas.

A arquitetura hexagonal foi inventada por Alistair Cockburn em 2005, em uma tentativa de evitar armadilhas estruturais conhecidas no design de software orientado a objetos (OOP), como dependências indesejadas entre camadas e a contaminação do código da interface do usuário com a lógica de negócios. O conceito de Arquitetura Hexagonal foi proposto por Alistair Cockburn, em meados dos anos 90, em um artigo postado na primeira wiki que foi desenvolvida, chamada WikiWikiWeb (cujos artigos tratavam principalmente de temas relacionados com Engenharia de Software).

<img width="2774" height="1582" alt="1_Bpi4Eynu38ayH-8ZE3cSKQ" src="https://github.com/user-attachments/assets/0a8ddc7c-628e-4569-804a-44ff990c38eb" />

Os objetivos de uma Arquitetura Hexagonal são parecidos com os de uma Arquitetura Limpa. Mas, para reforçar, a ideia é construir sistemas que favorecem reusabilidade de código, alta coesão, baixo acoplamento, independência de tecnologia e que são mais fáceis de serem testados. A arquitetura hexagonal, também conhecida como arquitetura de portas e adaptadores, pode ser combinada com outras arquiteturas e designs de software para criar sistemas mais robustos e flexíveis como a Arquitetura em Camadas (N-Tier/ Layered Architecture), SOA - Arquitetura Orientada a Serviços, Microservices, DDD - Domain-Driven Design, Arquitetura Limpa e CQRS - Command Query Responsibility Segregation.

Uma <a href="https://medium.com/codex/clean-architecture-for-dummies-df6561d42c94">Arquitetura Hexagonal</a> divide as classes de um sistema em dois grupos principais:

<img height="377" align="right" src="https://github.com/user-attachments/assets/02b41276-2062-4fc5-9ba0-11e3214c3753" />

- **Classes de domínio**, isto é, diretamente relacionadas com o negócio do sistema.

- **Classes relacionadas com infraestrutura**, tecnologias e responsáveis pela integração com sistemas externos (tais como bancos de dados).

Além disso, em uma Arquitetura Hexagonal, classes de domínio não devem depender de classes relacionadas com infraestrutura, tecnologias ou sistemas externos. A vantagem dessa divisão é desacoplar esses dois tipos de classes.

Assim, as classes de domínio não conhecem as tecnologias – bancos de dados, interfaces com usuário e quaisquer outras bibliotecas – usadas pelo sistema. Consequentemente, mudanças de tecnologia podem ser feitas sem impactar as classes de domínio. Talvez ainda mais importante, as classes de domínio podem ser compartilhadas por mais de uma tecnologia. Por exemplo, um sistema pode ter diversas interfaces (Web, mobile, etc).

Em uma arquitetura hexagonal, a comunicação entre as classes dos dois grupos é mediada por adaptadores, isto é, por classes que implementam o padrão de projeto de mesmo nome que estudamos no Capítulo 6. Iremos explicar melhor o papel dos adaptadores logo a seguir.

Visualmente, a arquitetura é representada por meio de dois hexágonos concêntricos (veja figura). No hexágono interno, ficam as classes do domínio (ou classes de negócio, se você preferir). No hexágono externo, ficam os adaptadores. Por fim, as classes de interface com o usuário, classes de tecnologia ou de sistemas externos ficam fora desses dois hexágonos.

Assim, o nome hexagonal tem sua origem na figura acima. Cockburn justifica o uso de um hexágono do seguinte modo:

> **"** Cada face do hexágono representa um motivo pelo qual o sistema deve se comunicar com o mundo exterior. É por isso que são hexágonos concêntricos e não círculos concêntricos.

Dentre os motivos que requerem comunicação com o mundo exterior podemos citar os seguintes: interagir com seus usuários (por meio de algum tipo de interface, seja ela gráfica, Web, mobile, terminal, etc), persistir informações, enviar informações para outros sistemas, etc.

Em uma Arquitetura Hexagonal, o termo **porta** (port) designa as interfaces usadas para comunicação com as classes de domínio (veja que interface aqui significa interface de programação; por exemplo, uma interface de Java).

<img width="729" height="464" alt="PortsAndAdapters" src="https://github.com/user-attachments/assets/d7f956c4-0b34-4ce9-9e44-c11c47f59d72" />

Existem dois tipos de portas:

- **Portas de entrada**: são interfaces usadas para comunicação de fora para dentro, isto é, quando uma classe externa precisa chamar um método de uma classe de domínio. Logo, essas portas declaram os serviços providos pelo sistema, isto é, serviços que o sistema oferece para o mundo exterior.

- **Portas de saída**: são interfaces usadas para comunicação de dentro para fora, isto é, quando uma classe de domínio precisa chamar um método de uma classe externa. Logo, essas portas declaram os serviços requeridos pelo sistema, isto é, serviços do mundo exterior que são necessários para o funcionamento do sistema.

O importante é que as portas são independentes de tecnologia. Portanto, elas estão localizadas no hexágono interior.

Por outro lado, os sistemas externos, normalmente, usam alguma tecnologia, seja ela de comunicação (REST, gRPC, GraphQL, etc), de bancos de dados (SQL, noSQL, etc), de interação com o usuário (Web, mobile, etc), etc.

Daí a necessidade de componentes localizados no hexágono mais externo da arquitetura – os adaptadores –, os quais atuam de um dos dois modos a seguir:

Eles recebem chamadas de métodos vindas de fora do sistema e encaminham essas chamadas para métodos adequados das portas de entrada.

<img width="972" height="927" alt="a1lup0ewj49dtu28q4d5" src="https://github.com/user-attachments/assets/fb00ac74-4643-4f32-8f29-609611514b18" />

Eles recebem chamadas vindas de dentro do sistema, isto é, das classes de domínio, e as direcionam para um sistema externo, tais como um banco de dados, um outro sistema da organização ou mesmo de terceiros.

A arquitetura hexagonal desempenha um papel significativo no projeto do sistema por vários motivos, particularmente no contexto de capacidade de manutenção, escalabilidade e flexibilidade. Aqui estão as principais razões pelas quais é importante:

- **Separação de preocupações**: a arquitetura impõe uma separação clara entre a lógica de negócios principal e os sistemas externos, como bancos de dados, APIs ou interfaces de usuário. Ao isolar o núcleo, ele garante que a lógica de negócios não esteja entrelaçada com a infraestrutura ou preocupações externas. Isso leva a um código mais limpo e modular, mais fácil de entender e manter.

- **Adaptabilidade e flexibilidade**: Um dos principais benefícios da arquitetura hexagonal é sua capacidade de se adaptar a mudanças em sistemas externos sem exigir mudanças na lógica de negócios principal. Por exemplo, se uma empresa decidir mudar de um banco de dados relacional para um banco de dados NoSQL, apenas o adaptador responsável pela interação do banco de dados precisa ser modificado. A lógica central permanece inalterada. Isso torna o sistema à prova de futuro e capaz de evoluir com as mudanças tecnológicas.

- **Estabilidade aprimorada**: como dependências externas, como bancos de dados ou APIs, são abstraídas, a lógica principal pode ser facilmente testada por unidade sem a necessidade de simulações ou stubs complexos. O uso de portas e adaptadores permite simular interfaces para sistemas externos, permitindo que o núcleo seja testado isoladamente. Isso leva a uma maior cobertura de teste e a um código mais confiável e livre de bugs.

- **Desenvolvimento desacoplado**: Diferentes equipes podem trabalhar de forma independente em várias partes do sistema. Uma equipe pode trabalhar na lógica de negócios principal, enquanto outra se concentra no desenvolvimento de adaptadores para APIs, bancos de dados ou outros sistemas externos. Essa natureza dissociada permite o desenvolvimento paralelo, acelerando o processo de desenvolvimento.

- **Componentes intercambiáveis**: A arquitetura hexagonal facilita a substituição ou integração de novos componentes sem afetar o sistema principal. Se uma nova API for introduzida ou se uma mais antiga for descontinuada, o adaptador que manipula essa API pode ser trocado sem perturbar a lógica de negócios central. Isso é especialmente útil em sistemas grandes e distribuídos, onde diferentes componentes estão em constante evolução.

A arquitetura hexagonal, também conhecida como arquitetura de portas e adaptadores, consiste em vários componentes-chave que trabalham juntos para criar um sistema flexível, desacoplado e sustentável. Aqui estão os principais componentes da Arquitetura Hexagonal:

1. **Entidades** (Core Business Logic): No coração da Arquitetura Hexagonal estão as Entidades, que representam a lógica de negócios principal e as regras do aplicativo. Essas entidades são completamente independentes de sistemas externos e permanecem isoladas de preocupações como bancos de dados ou interfaces de usuário. O objetivo é garantir que a lógica de negócios seja encapsulada e possa operar independentemente de como os dados são recebidos ou persistidos.

2. **Portas** (interfaces): As portas são as interfaces que definem como os sistemas externos se comunicam com a lógica principal. Essas portas atuam como limites entre o núcleo e o mundo exterior. Existem dois tipos de portas:
   - **Portas de entrada**: Defina como o mundo externo (como uma interface com o usuário, API ou fila de mensagens) pode interagir com o sistema principal. Eles são responsáveis por receber informações e acionar a lógica de negócios no núcleo.
   - **Portas de saída**: Defina como o sistema central interage com sistemas externos (como bancos de dados ou APIs externas) para enviar ou receber dados. Essas portas abstraem os detalhes de comunicação e garantem que o núcleo interaja apenas com componentes externos por meio dessas interfaces.

3. **Adaptadores** (Implementações de Portas): Adaptadores são a implementação das portas. Eles são responsáveis por traduzir dados externos (como solicitações HTTP, consultas de banco de dados ou mensagens de filas) em algo que o núcleo possa entender e vice-versa. Os adaptadores permitem que diferentes sistemas externos interajam com o sistema central sem que o núcleo esteja diretamente ciente das especificidades do sistema externo.
   - **Adaptadores de entrada**: Manipule a comunicação de fontes externas, como controladores HTTP, componentes de interface do usuário ou sistemas de mensagens, e converta-os em um formato compreendido pelo núcleo por meio de portas de entrada.
   - **Adaptadores de saída**: lidam com a comunicação com serviços externos ou bancos de dados, como implementações de repositório, APIs externas ou sistemas de armazenamento de dados. Eles pegam os dados do núcleo, processam-nos conforme necessário e os enviam para os sistemas externos apropriados.

4. **Serviços de Aplicação** (Interagentes/Casos de Uso) Os Serviços de Aplicativos, também conhecidos como Interagentes ou Casos de Uso, atuam como intermediários entre as entidades (lógica de negócios principal) e as camadas externas (portas e adaptadores). Esses serviços coordenam o fluxo de dados entre portas de entrada (por exemplo, solicitações de usuários) e portas de saída (por exemplo, fontes de dados). Eles contêm a lógica do aplicativo que orienta o processo de negócios, mas permanecem separados das principais regras de negócios.

Por exemplo, um Interactor pode obter a entrada do usuário de um formulário da Web (por meio de um adaptador de entrada), processá-la por meio de regras de negócios e, em seguida, persistir os resultados usando um repositório (por meio de um adaptador de saída).

![0_qLwWGERvZjcqs0ii](https://github.com/user-attachments/assets/3372d7a2-4d5e-4f72-b0c9-aa3374bfb780)

5. **Repositórios** (camada de persistência): Os repositórios são usados para gerenciar a persistência de dados. Eles fornecem uma camada entre a lógica principal e o sistema de armazenamento de dados (como um banco de dados). Os repositórios geralmente são implementados como adaptadores de saída que interagem com o banco de dados por meio de portas de saída. Eles encapsulam a lógica necessária para recuperar e armazenar dados em sistemas de armazenamento externos, permitindo que a lógica principal permaneça independente do banco de dados.

6. **Camada de transporte**: A camada de transporte lida com a comunicação entre usuários ou sistemas externos e o aplicativo. Isso pode incluir o tratamento de solicitações HTTP, filas de mensagens ou outras formas de operações de entrada/saída. A camada de transporte interage com os adaptadores de entrada para encaminhar solicitações ao sistema principal. Na Arquitetura Hexagonal, essa camada é desacoplada da lógica de negócios, permitindo que o sistema suporte vários mecanismos de comunicação (por exemplo, API REST, WebSocket, etc.).

7. **Sistemas Externos** (Infraestrutura): Os sistemas externos incluem bancos de dados, APIs, filas de mensagens e outros componentes de infraestrutura com os quais o aplicativo interage. Na arquitetura hexagonal, esses sistemas são conectados à lógica principal por meio de adaptadores e portas de saída, garantindo que o sistema central não tenha conhecimento dos detalhes do sistema externo.

A arquitetura hexagonal (arquitetura de portas e adaptadores) oferece várias vantagens no design do sistema, tornando-a uma escolha popular para a criação de sistemas flexíveis, sustentáveis e escaláveis. Aqui estão as principais vantagens:

- Separação de preocupações: A arquitetura hexagonal separa claramente a lógica de negócios principal de sistemas externos, como bancos de dados, APIs ou interfaces de usuário. Isso torna a lógica principal independente de como os dados são inseridos, armazenados ou exibidos, permitindo um código modular mais limpo.

- Flexibilidade e adaptabilidade: Ao desacoplar a lógica de negócios principal dos sistemas externos, a arquitetura permite flexibilidade na integração de novas tecnologias ou na substituição das antigas. Por exemplo, você pode alternar de um banco de dados SQL para um banco de dados NoSQL ou de uma API REST para uma API GraphQL, simplesmente alterando o adaptador correspondente, sem tocar na lógica principal.

- Estabilidade aprimorada: Como a lógica principal é isolada de sistemas externos, ela pode ser facilmente testada por unidade sem a necessidade de simular ou eliminar dependências complicadas, como bancos de dados ou serviços da Web. Os testes se tornam mais diretos e focados na funcionalidade principal, levando a uma melhor cobertura e sistemas mais confiáveis.

- Manutenção: A arquitetura hexagonal incentiva a modularidade, tornando o código mais fácil de entender e manter. Cada componente, seja a lógica principal, adaptadores ou portas, tem uma função bem definida e pode ser mantido separadamente. Isso reduz a chance de introduzir bugs ao modificar uma parte do sistema, pois as alterações são localizadas.

- Extensibilidade: novos recursos ou componentes podem ser adicionados ao sistema sem alterar a lógica principal existente. Por exemplo, se você precisar adicionar um novo tipo de interface (por exemplo, um novo sistema de mensagens ou API), basta criar um novo adaptador e porta para ele, deixando a lógica principal inalterada. Isso torna a arquitetura altamente extensível.

- Desenvolvimento paralelo: Diferentes equipes podem trabalhar em diferentes partes do sistema de forma independente. Uma equipe pode se concentrar no desenvolvimento da lógica de negócios principal, enquanto outras equipes trabalham em adaptadores específicos para
sistemas externos, como bancos de dados, APIs ou filas de mensagens. Esse desacoplamento permite um desenvolvimento mais rápido e maior colaboração.

Embora a arquitetura hexagonal ofereça inúmeros benefícios, ela também apresenta certos desafios no design do sistema. Esses desafios precisam ser considerados cuidadosamente ao implementar essa arquitetura:

<img width="1100" height="752" alt="0_IL8vujFMMgXa0Hsa" src="https://github.com/user-attachments/assets/62599d58-9641-4213-a3dd-8c68d6b98718" />

1. Maior complexidade no início: a arquitetura hexagonal introduz camadas adicionais, como portas, adaptadores e serviços de aplicativos, o que pode tornar o projeto inicial mais complexo. Os desenvolvedores podem precisar escrever mais código clichê para criar interfaces (portas) e adaptadores, fazendo com que o sistema pareça mais complexo do que arquiteturas mais simples, especialmente para aplicativos pequenos ou diretos.

2. Curva de aprendizado: Para equipes não familiarizadas com a arquitetura, pode haver uma curva de aprendizado íngreme. Entender como estruturar o sistema usando portas, adaptadores e a separação de preocupações pode levar tempo, e os desenvolvedores precisam se familiarizar com novos padrões e princípios de design. Isso pode retardar o processo de desenvolvimento inicialmente.

3. Sobrecarga para aplicativos simples: Para aplicativos pequenos e simples, a arquitetura hexagonal pode introduzir complexidade desnecessária. Os benefícios do desacoplamento, da capacidade de teste e da modularidade podem não valer a sobrecarga adicional de projetar o sistema de maneira hexagonal. Aplicativos mais simples podem ser melhor atendidos com arquiteturas menos complexas, como MVC ou arquitetura em camadas.

4. Dificuldade em gerenciar vários adaptadores: À medida que o sistema cresce, pode ser necessário oferecer suporte a várias interfaces externas, como diferentes APIs, bancos de dados ou interfaces de usuário. O gerenciamento desses adaptadores pode se tornar complicado, pois cada um requer sua própria implementação. Manter o controle de vários adaptadores e mantê-los pode aumentar a complexidade do sistema.

5. Mais abstrações para gerenciar: A arquitetura hexagonal envolve várias camadas de abstração - portas, adaptadores, entidades, interagentes - cada uma responsável por diferentes aspectos do sistema. Embora essas abstrações sejam essenciais para o desacoplamento, às vezes elas podem dificultar os problemas de depuração e rastreamento, pois você precisa navegar por várias camadas para entender o fluxo de dados e a lógica.

A implementação da arquitetura hexagonal requer uma estratégia cuidadosa para garantir que o sistema mantenha seus benefícios de flexibilidade, desacoplamento e capacidade de manutenção. Aqui estão as principais estratégias para implementar com sucesso a arquitetura hexagonal no projeto do sistema:

1. Comece com a Lógica de Domínio Principal (Entidades): Defina a lógica de negócios principal: comece implementando a lógica de negócios principal (entidades). A parte central da Arquitetura Hexagonal é o modelo de domínio, que deve permanecer independente de sistemas externos, como bancos de dados, APIs ou interfaces de usuário. Isso garante que as regras de negócios estejam no centro do sistema e não sejam afetadas por alterações na infraestrutura.

2. Foco no DDD (Design Controlado por Domínio): o uso dos princípios do DDD ajuda a moldar um modelo de domínio avançado que reflete os requisitos de negócios. Isso garante que a lógica principal seja autossuficiente e possa ser reutilizada em diferentes contextos.

3. Projete as portas (interfaces): Identifique as portas de entrada e saída: Depois que a lógica principal for estabelecida, defina as portas de entrada (como o mundo externo interage com o sistema) e as portas de saída (como o sistema interage com sistemas externos, como bancos de dados ou serviços externos).

4. Dependências externas abstratas: as portas devem definir interfaces que abstraem os detalhes de dependências externas, como bancos de dados, APIs ou filas de mensagens. Isso ajuda a manter a lógica principal isolada de quaisquer detalhes específicos da infraestrutura.

5. Adaptadores de implemento (conectando sistemas externos): Desenvolver adaptadores para portas de entrada: Implemente adaptadores de entrada que convertem entradas externas (como solicitações HTTP, comandos CLI ou eventos de filas de mensagens) no formato exigido pela lógica principal. Por exemplo, use um controlador HTTP como um adaptador de entrada para lidar com solicitações REST e roteá-las para o sistema núcleo.

6. Desenvolver adaptadores para portas de saída: Implemente adaptadores de saída que se conectam a sistemas externos (como um banco de dados ou APIs externas). Esses adaptadores lidam com a comunicação com esses sistemas externos, mas permanecem abstraídos da lógica de negócios principal.

7. Isolar infraestrutura: mantenha a lógica de infraestrutura (por exemplo, interações de banco de dados ou clientes de API) contida nos adaptadores de saída, garantindo que a lógica principal não esteja ciente das especificidades do sistema externo.

8. Aproveite a injeção de dependência: Desacoplar núcleo dos adaptadores: use a injeção de dependência para injetar os adaptadores na lógica principal. Isso garante que o sistema principal dependa apenas de abstrações (portas) e não de implementações concretas (adaptadores).

9. Injetar adaptadores por meio de construtores ou fábricas: implemente a injeção de adaptador usando construtores ou fábricas, garantindo que a lógica principal permaneça testável e adaptável. Esse padrão dá suporte à troca de adaptadores diferentes com impacto mínimo na lógica principal.

10. Serviços de aplicativos de design (interactianos): Coordenar casos de uso: use serviços de aplicativos ou interagentes para implementar os principais casos de uso do aplicativo. Esses serviços atuam como intermediários entre as portas de entrada (solicitações do usuário) e as portas de saída (fontes de dados ou APIs externas). Mantenha a lógica de negócios central: certifique-se de que os interagentes não contenham a lógica de negócios por conta própria, mas coordenem as interações entre as principais regras de negócios e o mundo exterior.

11. Encapsular o acesso a dados em repositórios: Lógica de persistência abstrata: Implemente repositórios como adaptadores de saída que gerenciam interações de banco de dados. Os repositórios encapsulam a lógica de acesso a dados, permitindo que a lógica principal permaneça independente das especificidades do banco de dados.

12. Use repositórios orientados por interface: defina repositórios como interfaces na camada central e implemente a lógica real de acesso a dados na camada de infraestrutura (usando ORMs, consultas SQL etc.).

Casos de uso da arquitetura hexagonal: A arquitetura hexagonal é particularmente benéfica em uma variedade de casos de uso de projeto de sistema em que flexibilidade, desacoplamento e capacidade de manutenção são cruciais.

Abaixo estão alguns dos principais casos de uso em que a Arquitetura Hexagonal pode ser aplicada:

- Construindo aplicativos da Web flexíveis: No desenvolvimento de aplicativos da Web, a arquitetura hexagonal permite separar a lógica de negócios das preocupações de infraestrutura, como estruturas da Web ou bancos de dados. Isso torna o aplicativo mais flexível para se adaptar a alterações, como troca de estruturas, integração com novas tecnologias de front-end ou alteração de mecanismos de armazenamento de dados.

- Arquitetura de microsserviços: em microsserviços, diferentes serviços geralmente interagem entre si, bancos de dados ou APIs de terceiros. A Hexagonal Architecture garante que os microsserviços sejam isolados, com o núcleo de cada serviço sendo completamente desacoplado de suas dependências. Isso também permite que os serviços sejam facilmente substituídos ou dimensionados sem afetar a lógica de negócios principal.

- Sistemas orientados a eventos: os sistemas orientados a eventos dependem muito da comunicação assíncrona por meio de filas de mensagens (como RabbitMQ ou AWS SQS). O HexagonalArchitecture permite que a lógica de negócios principal permaneça independente de se os eventos vêm de HTTP, WebSocket ou filas de mensagens, pois cada tipo de interação pode ser tratado por diferentes adaptadores de entrada.

- Sistemas com várias interfaces de usuário: quando um aplicativo precisa oferecer suporte a várias interfaces de usuário (por exemplo, web, móvel, desktop, CLI), a arquitetura hexagonal permite que a lógica de negócios principal seja compartilhada em todas as plataformas. Adaptadores diferentes podem ser criados para cada tipo de interface do usuário sem duplicar a lógica principal.

- Desenvolvimento orientado a testes (TDD) e testes unitários: a arquitetura hexagonal é particularmente adequada para TDD e testes unitários porque a lógica de negócios principal é isolada das preocupações com a infraestrutura. O modelo de portas e adaptadores permite simular facilmente sistemas externos, tornando os testes de unidade mais simples de escrever e manter.

A arquitetura hexagonal, também conhecida como arquitetura de portas e adaptadores, foi aplicada com sucesso em vários projetos do mundo real em diferentes domínios. Aqui estão alguns exemplos notáveis:

- **Shopify**: A lógica de negócios principal da Shopify é dissociada de vários gateways de pagamento, provedores de remessa e outros serviços por meio de adaptadores. Isso permite que os comerciantes alternem entre diferentes opções de pagamento e integrem vários serviços sem afetar as principais funcionalidades da plataforma.

- **PayPal**: o PayPal usa a Hexagonal Architecture para separar sua lógica principal de processamento de transações dos vários serviços externos com os quais interage, como diferentes APIs bancárias, sistemas de detecção de fraudes e interfaces de usuário. Isso permite que o PayPal se adapte perfeitamente às mudanças nos regulamentos ou integrações.

- **WordPress**: O WordPress implementa a Arquitetura Hexagonal permitindo que os plug-ins interajam com suas principais funcionalidades sem acoplá-las fortemente. Isso permite que os desenvolvedores estendam o CMS com vários plug-ins (para SEO, análises, etc.) que atuam como adaptadores para a lógica principal.

- **Netflix**: A Netflix utiliza a Hexagonal Architecture para gerenciar seus vários microsserviços para entrega de conteúdo, recomendações de usuários e processamento de pagamentos. Cada serviço pode interagir com sistemas externos (como redes de distribuição de conteúdo) por meio de adaptadores, permitindo que eles sejam dimensionados de forma independente.

- **Epic Systems**: A Epic usa a Hexagonal Architecture para desacoplar seu sistema de gerenciamento clínico de vários sistemas externos (como laboratórios, farmácias e outros prestadores de serviços de saúde). Isso garante que as mudanças nos sistemas externos não interrompam as principais funcionalidades de gerenciamento de integridade.

<img width="1400" height="985" alt="0_0E7BeQX8VXDT21Ix" src="https://github.com/user-attachments/assets/76c0faab-9403-402c-9695-dcc0e00194aa" />

Em conclusão, a Arquitetura Hexagonal é uma abordagem de design poderosa que aumenta a flexibilidade e a capacidade de manutenção dos sistemas de software. Ao separar a lógica de negócios principal das dependências externas, ele permite que os desenvolvedores se adaptem facilmente às mudanças e integrem novas tecnologias sem interromper o aplicativo principal. Essa arquitetura promove melhores práticas de teste e simplifica o processo de desenvolvimento. Seja aplicada a aplicativos da web, microsserviços ou integrações de sistemas legados, a Hexagonal Architecture oferece uma maneira estruturada de criar soluções resilientes e escaláveis que podem evoluir com as necessidades de usuários e empresas.

HexagonalArchCQRSTDD
