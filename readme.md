# Atividade Final do Curso: Modelagem de Eventos - Supermercado do Futuro

![img](https://raw.githubusercontent.com/Secol/fiap-amd-event-modeling/main/images/01.png)

## Descrição da Atividade

Nesta atividade, vocês serão desafiados a realizar uma Modelagem de Eventos para a solução proposta no projeto "Supermercado do Futuro". Utilizando os insights e conceitos discutidos e registrados durante o brainstorming (documentado abaixo), o objetivo é criar um modelo que detalhe os eventos chave do sistema, desde a entrada do cliente no supermercado até a conclusão da compra e saída do estabelecimento.

## Instruções

__Formação de Grupos:__ A atividade pode ser realizada individualmente ou em grupos. Recomenda-se a formação dos mesmos grupos da **Startup One**, para facilitar a colaboração e a continuidade do trabalho em equipe.

__Desenvolvimento da Modelagem:__ Utilize ferramentas de design de eventos, como diagramas ou softwares específicos de modelagem, para representar os eventos identificados durante o brainstorming.

- [Miro](https://miro.com/pt/)
- [google Jamboard](https://jamboard.google.com/)
- [LucidChart](https://www.lucidchart.com/)

__Elaboração do Board Final:__ Ao concluir a modelagem, organize os eventos em um board lógico e coeso que represente o fluxo completo da experiência do cliente no "Supermercado do Futuro". Vocês podem utilizar o [exemplo apresentado em aula](https://raw.githubusercontent.com/Secol/fiap-amd-event-modeling/main/images/02.png) como referência para a atividade.

__Envio da Atividade:__ Dois possíveis meios de entrega, sendo:

- O grupo deverá exportar uma imagem em alta resolução do board final.
- O grupo deverá publicar a imagem para acesso do professor na atividade cadastrada através do Portal do Aluno.

Certifique-se de que a imagem esteja clara e os eventos sejam facilmente identificáveis. Em caso de dúvidas durante a execução, utilize o e-mail proffernando.secol@fiap.com.br para qualquer esclarecimento necessário.

## Critérios de Avaliação

__Clareza e Coerência:__ A modelagem deve ser clara e lógica, com uma sequência coerente de eventos que reflita fielmente o fluxo proposto no brainstorming.

__Completude:__ Todos os eventos-chave discutidos devem estar representados e devidamente detalhados.

__Qualidade Visual:__ A imagem enviada deve ser de alta resolução, com boa legibilidade e organização dos elementos.

# Brainstorming "Supermercado do Futuro"

## Acesso e Identificação do Cliente

__Entrada via QR Code e Reconhecimento Facial:__ Ao chegar, o cliente escaneia um QR code e passa por um reconhecimento facial para acessar o supermercado. Um evento é registrado indicando a entrada do cliente.

Os seguintes detalhes foram fornecidos pelo time de engenharia:  

1. Ao chegar na loja, o cliente visualiza um QR Code exibido em um monitor localizado na entrada.  
2. Em seguida, ele acessa o aplicativo do supermercado e escaneia o QR Code.  
3. O sistema do supermercado valida o QR Code, inicia uma sessão de compra e solicita a identificação facial do cliente.  
4. No mesmo monitor onde o QR Code foi escaneado, uma câmera captura a imagem do rosto do cliente.  
5. Essa imagem é então enviada para um servidor no backend da solução, onde é processada e encaminhada para um parceiro responsável pela validação facial.  
6. O parceiro retorna o resultado da validação, que pode ser positiva ou negativa:  
   - Se a validação for positiva, o cliente é autorizado a entrar no supermercado.  
   - Se a validação for negativa, o acesso ao supermercado é negado.  
7. Em caso de autorização, um serviço se comunica com o dispositivo de controle de acesso, acionando a liberação da catraca para a entrada do cliente. 

## Experiência de Compras Personalizada

__Navegação Otimizada com Lista de Compras:__ O aplicativo do cliente se comunica com o sistema do supermercado para sincronizar a lista de compras com as ofertas do dia e a disposição dos produtos, criando uma rota otimizada de compras.

Os seguintes detalhes foram fornecidos pelo time de engenharia:

1. O cliente pode utilizar o aplicativo do supermercado para criar uma lista de compras personalizada.  
2. Essa lista é automaticamente sincronizada com o backend da solução.  
3. No backend, a lista de compras é processada e combinada com as ofertas do dia e a disposição dos produtos na loja. Para isso, é utilizado um modelo de busca otimizada desenvolvido pelo time de Dados.  
   - Esse modelo possui uma política de parada que limita o tempo de processamento a no máximo 15 segundos para definir a rota de compras ideal. Além disso, é fundamental garantir o correto armazenamento das requisições (solicitações de outros clientes) de uso desse serviço.
4. A rota otimizada é então enviada para o aplicativo do cliente, permitindo que ele siga o caminho mais eficiente para encontrar os produtos desejados na loja.

## Interatividade e Informações de Produto

__Consulta de Produtos via Smartphone:__ Os clientes podem usar seus smartphones para escanear produtos, obtendo informações detalhadas como preço, receitas e dados nutricionais, graças a um sistema de reconhecimento de imagem no servidor local do supermercado.

Os seguintes detalhes foram fornecidos pelo time de engenharia:  

1. O cliente pode utilizar o aplicativo do supermercado para escanear produtos e acessar informações detalhadas.
2. O escaneamento é realizado pela câmera do smartphone, que captura a imagem do produto e a envia para um servidor local instalado na unidade do supermercado.
3. No servidor, um sistema de reconhecimento de imagem processa a foto e identifica o produto, retornando informações como preço, receitas sugeridas e dados nutricionais.
4. Como o servidor possui capacidade computacional limitada, um broker de mensageria é utilizado na infraestrutura local para garantir o armazenamento das requisições e a comunicação entre os serviços.
5. Após o processamento, as informações são enviadas de volta para o aplicativo do cliente, que as exibe na tela.

## Segurança e Monitoramento de Produtos

__Carrinhos e Cestas Inteligentes:__ Equipamentos com sensores para detectar o peso dos produtos inseridos, visando melhorar a precisão do inventário e prevenir perdas, integrando esses dados ao perfil de compra do cliente.

Os seguintes detalhes foram fornecidos pelo time de engenharia:

1. Cada carrinho ou cesta de compras é equipado com sensores de peso e tecnologia RFID, permitindo a detecção dos produtos adicionados ou removidos e o rastreamento do inventário em tempo real.
2. Quando o cliente insere ou retira um item do carrinho, os sensores capturam tanto o peso quanto a identificação do produto.
3. Essas informações são enviadas para o backend do supermercado, onde são processadas e vinculadas à sessão do cliente durante sua visita ao estabelecimento.

## Pagamento e Saída

2. __Pagamento Integrado e Saída Segura:__ Ao finalizar a compra, o cliente realiza o pagamento através de um gateway integrado. Uma nota fiscal digital é enviada para o aplicativo do cliente, que pode então sair do supermercado após uma nova validação facial.

Os seguintes detalhes foram fornecidos pelo time de engenharia:  

1. Ao finalizar a compra, o cliente dirige-se a um caixa de autoatendimento, onde o sistema verifica se o peso e os itens do carrinho correspondem ao que foi registrado durante sua visita.
2. O backend se comunica com um parceiro de pagamento, que retorna uma sessão segura para a transação.
3. Essa sessão é enviada para o sistema do caixa de autoatendimento, que exibe ao cliente as opções de pagamento disponíveis.
4. O cliente seleciona a forma de pagamento e conclui a transação.
5. Após a confirmação do pagamento, uma nota fiscal digital é gerada e enviada para o aplicativo do cliente.
6. Na saída, o cliente passa por uma nova validação facial seguindo o mesmo fluxo detalhado no item __Entrada via QR Code e Reconhecimento Facial__, que autoriza a liberação da catraca para deixar o estabelecimento.