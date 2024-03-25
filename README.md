# jupyter-k8s

## Bora entender o que é kubernetes?

Conceito geral:

 Kubernetes, muitas vezes abreviado como K8s, é uma plataforma de código aberto para automatizar a implantação, o dimensionamento e a gestão de aplicações em contêineres. Basicamente, é como um gerente de restaurante que cuida de todos os seus clientes (aplicações) sem que você precise se preocupar com os detalhes de como cada um é atendido.

Na prática do dia a dia:

Imagine que você é um chef de cozinha que precisa gerenciar uma equipe de cozinheiros (aplicações) que trabalham em um restaurante. Cada cozinheiro é especializado em um tipo de prato (aplicação). Por exemplo, temos o Chef de Sopas, o Chef de Carnes, o Chef de Vegetais, etc.

Um dia, o restaurante recebe um grande pedido de clientes que querem todos os pratos ao mesmo tempo. Você, como chef, precisa garantir que cada cozinheiro tenha o que precisa para preparar seus pratos sem sobrecarregar ninguém. Aqui é onde entra Kubernetes.

Você usa Kubernetes para gerenciar a equipe de cozinheiros, garantindo que cada um tenha o que precisa para trabalhar eficientemente. Por exemplo, se o Chef de Sopas está ocupado, Kubernetes pode redirecionar alguns pedidos para o Chef de Carnes, que tem menos carga de trabalho. Se um cozinheiro precisa de mais ingredientes, Kubernetes pode automaticamente aumentar a quantidade de ingredientes disponíveis para ele.

E aí, você está pronto para o grande dia? Claro, porque você tem Kubernetes cuidando de tudo por você. E o melhor de tudo é que, se algo der errado, Kubernetes pode até mesmo "chamar um cozinheiro substituto" para substituir o cozinheiro que está com problemas, garantindo que o restaurante continue funcionando sem problemas.

Então, em resumo, Kubernetes é como um gerente de restaurante que cuida de todos os detalhes para que você possa se concentrar em cozinhar os melhores pratos possíveis. E, assim como um bom gerente de restaurante, Kubernetes é capaz de lidar com qualquer situação, garantindo que tudo funcione perfeitamente.

### E lá vamos nós: passo a passo!

### Namespace

Um `namespace` no Kubernetes é uma forma de agrupar e isolar recursos dentro de um cluster. Isso permite organizar os recursos de maneira lógica e segura, facilitando a gestão e a segurança dos recursos do Kubernetes.

O que eu ganho quando crio um `Namespace`?

1. Organização: `Namespaces` permitem que você organize seus recursos do Kubernetes de maneira lógica. Por exemplo, você pode ter um namespace para desenvolvimento, outro para testes e outro para produção. Isso facilita a gestão de recursos em diferentes ambientes.
2. Segurança: `Namespaces` também ajudam a melhorar a segurança, pois você pode definir políticas de segurança específicas para cada namespace. Isso significa que você pode controlar quem tem acesso a quais recursos dentro de um namespace específico.
3. Gerenciamento de Recursos: `Namespaces` permitem que você gerencie recursos de forma mais eficiente. Por exemplo, você pode limitar a quantidade de recursos (como CPU e memória) que podem ser usados em um namespace específico. Isso é útil para evitar que um único namespace consuma todos os recursos disponíveis no cluster.
4. Facilidade de Uso: Trabalhar com `namespaces` pode tornar o gerenciamento de recursos no Kubernetes mais fácil e intuitivo. Em vez de gerenciar todos os recursos em um cluster grande, você pode focar em um namespace de cada vez.
5. Evitar Conflitos de Nomes: `Namespaces` ajudam a evitar conflitos de nomes entre recursos. Por exemplo, você pode ter dois serviços com o mesmo nome em diferentes `namespaces` sem conflitos.

### Deployment

Um `Deployment` no Kubernetes é uma forma de gerenciar e atualizar aplicações que estão sendo executadas em um cluster. Ele é responsável por garantir que um número específico de réplicas de uma aplicação esteja sempre em execução. Se uma réplica falhar, o `Deployment` automaticamente substitui essa réplica para manter o número desejado de réplicas.

O que eu ganho quando crio um `deployment`?

1. Réplicas: Um `Deployment` garante que um número específico de réplicas de uma aplicação esteja sempre em execução. Se uma réplica falhar, o `Deployment` substitui essa réplica automaticamente.
2. Atualizações: O `Deployment` permite atualizar a aplicação de forma controlada. Você pode especificar uma nova imagem de contêiner para a aplicação e o `Deployment` irá atualizar as réplicas existentes para a nova imagem, garantindo que a aplicação continue funcionando sem interrupções.
3. Rollback: Se uma atualização falhar ou se você decidir que a nova versão da aplicação não é adequada, o `Deployment` permite que você reverta para uma versão anterior da aplicação.
4. Escalabilidade: Você pode facilmente aumentar ou diminuir o número de réplicas de uma aplicação usando o `Deployment`. Isso é útil para gerenciar a carga de trabalho da aplicação.
5. Self-healing: O `Deployment` garante que a aplicação continue funcionando mesmo em caso de falhas. Se uma réplica falhar, o `Deployment` substitui essa réplica automaticamente.

Remusão: Em resumo, um `Deployment` no Kubernetes é uma maneira de gerenciar aplicações de forma que elas estejam sempre disponíveis e atualizadas, com a capacidade de escalar facilmente e de se recuperar de falhas.




