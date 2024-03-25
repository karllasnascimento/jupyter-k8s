# jupyter-k8s

## Bora entender o que é k8s com a k5s?

**Conceito geral:**

 Kubernetes, muitas vezes abreviado como K8s, é uma plataforma de código aberto para automatizar a implantação, o dimensionamento e a gestão de aplicações em contêineres. Basicamente, é como um gerente de restaurante que cuida de todos os seus clientes (aplicações) sem que você precise se preocupar com os detalhes de como cada um é atendido.

**Na prática do dia a dia:**

Imagine que você é um chef de cozinha que precisa gerenciar uma equipe de cozinheiros (aplicações) que trabalham em um restaurante. Cada cozinheiro é especializado em um tipo de prato (aplicação). Por exemplo, temos o Chef de Sopas, o Chef de Carnes, o Chef de Vegetais, etc.

Um dia, o restaurante recebe um grande pedido de clientes que querem todos os pratos ao mesmo tempo. Você, como chef, precisa garantir que cada cozinheiro tenha o que precisa para preparar seus pratos sem sobrecarregar ninguém. Aqui é onde entra Kubernetes.

Você usa Kubernetes para gerenciar a equipe de cozinheiros, garantindo que cada um tenha o que precisa para trabalhar eficientemente. Por exemplo, se o Chef de Sopas está ocupado, Kubernetes pode redirecionar alguns pedidos para o Chef de Carnes, que tem menos carga de trabalho. Se um cozinheiro precisa de mais ingredientes, Kubernetes pode automaticamente aumentar a quantidade de ingredientes disponíveis para ele.

E aí, você está pronto para o grande dia? Claro, porque você tem Kubernetes cuidando de tudo por você. E o melhor de tudo é que, se algo der errado, Kubernetes pode até mesmo "chamar um cozinheiro substituto" para substituir o cozinheiro que está com problemas, garantindo que o restaurante continue funcionando sem problemas.

Então, em resumo, Kubernetes é como um gerente de restaurante que cuida de todos os detalhes para que você possa se concentrar em cozinhar os melhores pratos possíveis. E, assim como um bom gerente de restaurante, Kubernetes é capaz de lidar com qualquer situação, garantindo que tudo funcione perfeitamente.

### E lá vamos nós: passo a passo!

### Namespace

Um `namespace` no Kubernetes é uma forma de agrupar e isolar recursos dentro de um cluster. Isso permite organizar os recursos de maneira lógica e segura, facilitando a gestão e a segurança dos recursos do Kubernetes.

O que eu ganho quando crio um `Namespace`?

1. **Organização**: `Namespaces` permitem que você organize seus recursos do Kubernetes de maneira lógica. Por exemplo, você pode ter um namespace para desenvolvimento, outro para testes e outro para produção. Isso facilita a gestão de recursos em diferentes ambientes.
2. **Segurança**: `Namespaces` também ajudam a melhorar a segurança, pois você pode definir políticas de segurança específicas para cada namespace. Isso significa que você pode controlar quem tem acesso a quais recursos dentro de um namespace específico.
3. **Gerenciamento de Recursos**: `Namespaces` permitem que você gerencie recursos de forma mais eficiente. Por exemplo, você pode limitar a quantidade de recursos (como CPU e memória) que podem ser usados em um namespace específico. Isso é útil para evitar que um único namespace consuma todos os recursos disponíveis no cluster.
4. **Facilidade de Uso**: Trabalhar com `namespaces` pode tornar o gerenciamento de recursos no Kubernetes mais fácil e intuitivo. Em vez de gerenciar todos os recursos em um cluster grande, você pode focar em um namespace de cada vez.
5. **Evitar Conflitos de Nomes**: `Namespaces` ajudam a evitar conflitos de nomes entre recursos. Por exemplo, você pode ter dois serviços com o mesmo nome em diferentes `namespaces` sem conflitos.

### Deployment

Um `Deployment` no Kubernetes é uma forma de gerenciar e atualizar aplicações que estão sendo executadas em um cluster. Ele é responsável por garantir que um número específico de réplicas de uma aplicação esteja sempre em execução. Se uma réplica falhar, o `Deployment` automaticamente substitui essa réplica para manter o número desejado de réplicas.

O que eu ganho quando crio um `deployment`?

1. **Réplicas**: Um `Deployment` garante que um número específico de réplicas de uma aplicação esteja sempre em execução. Se uma réplica falhar, o `Deployment` substitui essa réplica automaticamente.
2. **Atualizações**: O `Deployment` permite atualizar a aplicação de forma controlada. Você pode especificar uma nova imagem de contêiner para a aplicação e o `Deployment` irá atualizar as réplicas existentes para a nova imagem, garantindo que a aplicação continue funcionando sem interrupções.
3. **Rollback**: Se uma atualização falhar ou se você decidir que a nova versão da aplicação não é adequada, o `Deployment` permite que você reverta para uma versão anterior da aplicação.
4. **Escalabilidade**: Você pode facilmente aumentar ou diminuir o número de réplicas de uma aplicação usando o `Deployment`. Isso é útil para gerenciar a carga de trabalho da aplicação.
5. **Self-healing**: O `Deployment` garante que a aplicação continue funcionando mesmo em caso de falhas. Se uma réplica falhar, o `Deployment` substitui essa réplica automaticamente.

**Resumão**: Em resumo, um `Deployment` no Kubernetes é uma maneira de gerenciar aplicações de forma que elas estejam sempre disponíveis e atualizadas, com a capacidade de escalar facilmente e de se recuperar de falhas.

### Service

O Service no Kubernetes é um objeto que define uma política de acesso a um conjunto de Pods. Ele permite que você exponha um conjunto de Pods como um serviço de rede, tornando-os acessíveis de dentro ou fora do cluster.

### Tipos de Service:

**ClusterIP**: O tipo padrão. Exponha o serviço no cluster interno. Outros serviços no cluster podem acessá-lo usando o IP do serviço.
**NodePort**: Exponha o serviço na porta de cada nó do cluster. O serviço pode ser acessado externamente.
**LoadBalancer**: Exponha o serviço externamente usando um balanceador de carga.
**ExternalName**: Mapeia o serviço para um nome DNS externo.

O que eu ganho quando crio um `service`?

1. **Seletores de Rótulos**: Os Services usam seletores de rótulos para determinar quais Pods devem ser incluídos no serviço. Esses seletores correspondem aos rótulos definidos nos Pods.
2. **Discovery de Serviço**: O Kubernetes fornece mecanismos para descobrir serviços, como DNS interno e etcd. Isso permite que os Pods se comuniquem entre si usando nomes de serviço em vez de endereços IP.
3. **Balanceamento de Carga**: Para serviços que precisam de balanceamento de carga, o Kubernetes pode distribuir o tráfego entre os Pods de forma eficiente.
4. **Escalabilidade**: Como os Services são uma abstração sobre os Pods, eles facilitam a escalabilidade dos aplicativos. Se você precisar adicionar mais Pods para lidar com a carga, o Service pode direcionar automaticamente o tráfego para os novos Pods.

## Create x apply... quem ganha?

No Kubernetes, `kubectl create` e `kubectl apply` são comandos usados para criar ou atualizar recursos, mas eles têm diferenças significativas em termos de como operam e são usados. Vamos explorar essas diferenças de forma simplificada:

### `kubectl create`

- **Uso**: `kubectl create` é usado para criar novos recursos no cluster Kubernetes. Por exemplo, você pode usar `kubectl create deployment` para criar um novo deployment.
- **Comportamento**: Quando você executa `kubectl create`, o Kubernetes cria o recurso exatamente como você especificou no arquivo de configuração. Se o recurso já existir, o comando falhará, pois você não pode criar um recurso que já existe.
- **Exemplo**: Se você tentar criar um deployment que já existe, receberá um erro.

### `kubectl apply`

- **Uso**: `kubectl apply` é usado para aplicar configurações a recursos existentes ou criar novos recursos se eles não existirem. É mais comum usá-lo para atualizar recursos existentes.
- **Comportamento**: Quando você executa `kubectl apply`, o Kubernetes verifica se o recurso já existe. Se existir, ele atualiza o recurso com as configurações fornecidas, preservando as configurações que não foram alteradas. Se o recurso não existir, ele criará um novo recurso com as configurações fornecidas.
- **Exemplo**: Se você tiver um deployment e quiser atualizar o número de réplicas, pode usar `kubectl apply` para fazer essa alteração. O Kubernetes atualizará o deployment existente com o novo número de réplicas, mantendo todas as outras configurações inalteradas.

### Resumo

- **`kubectl create`** é mais adequado para cenários em que você sabe que o recurso não existe e deseja criá-lo. É útil para a criação inicial de recursos.
- **`kubectl apply`** é mais versátil e é preferido para atualizações de recursos existentes, pois permite que você mantenha as configurações existentes e aplique apenas as alterações desejadas.

### Exemplo

Imagine que você é um chef de cozinha e está tentando adicionar um novo prato ao menu. Se você já tem o prato no menu e quer fazer uma pequena alteração, como aumentar a quantidade de ingredientes, você usaria `kubectl apply` para fazer essa alteração. Mas se você está tentando adicionar um prato completamente novo ao menu, você usaria `kubectl create`.

Então, a diferença entre `kubectl create` e `kubectl apply` é como você adiciona um novo prato ao menu (cria um novo recurso) versus como você atualiza um prato existente (atualiza um recurso existente).

## Comandos úteis

O Kubernetes é uma plataforma de orquestração de contêineres que automatiza a implantação, o dimensionamento e a gestão de aplicativos em contêineres. Aqui estão alguns comandos úteis do Kubernetes (kubectl) e um cenário de uso para cada um.

### 1. `kubectl get pods`

**Cenário de Uso:** Você está tentando verificar o status dos pods em execução no seu cluster Kubernetes.

```bash
kubectl get pods
```

### 2. `kubectl describe pod <nome-do-pod>`

**Cenário de Uso:** Você precisa de detalhes sobre um pod específico, como eventos, logs e configurações.

```bash
kubectl describe pod my-app-pod
```

### 3. `kubectl logs <nome-do-pod>`

**Cenário de Uso:** Você quer ver os logs de um pod para depuração ou monitoramento.

```bash
kubectl logs my-app-pod
```

### 4. `kubectl exec -it <nome-do-pod> -- /bin/bash`

**Cenário de Uso:** Você precisa acessar o shell de um pod para executar comandos diretamente.

```bash
kubectl exec -it my-app-pod -- /bin/bash
```

### 5. `kubectl apply -f <arquivo.yaml>`

**Cenário de Uso:** Você está criando ou atualizando recursos no cluster Kubernetes a partir de um arquivo de configuração YAML.

```bash
kubectl apply -f my-app-deployment.yaml
```

### 6. `kubectl delete -f <arquivo.yaml>`

**Cenário de Uso:** Você está removendo recursos do cluster Kubernetes definidos em um arquivo de configuração YAML.

```bash
kubectl delete -f my-app-deployment.yaml
```

### 7. `kubectl scale deployment <nome-do-deployment> --replicas=<número-de-replicas>`

**Cenário de Uso:** Você precisa escalar um deployment para aumentar ou diminuir o número de réplicas.

```bash
kubectl scale deployment my-app-deployment --replicas=3
```

### 8. `kubectl rollout status deployment <nome-do-deployment>`

**Cenário de Uso:** Você quer verificar o status de uma atualização de deployment.

```bash
kubectl rollout status deployment my-app-deployment
```

### 9. `kubectl rollout undo deployment <nome-do-deployment>`

**Cenário de Uso:** Você precisa reverter para uma versão anterior de um deployment.

```bash
kubectl rollout undo deployment my-app-deployment
```

### 10. `kubectl get services`

**Cenário de Uso:** Você quer ver todos os serviços expostos no seu cluster Kubernetes.

```bash
kubectl get services
```
