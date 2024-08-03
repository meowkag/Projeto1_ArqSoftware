# Projeto1_ArqSoftware
Projeto 1 (Padrões de projeto e refatoração)

## 1. Padrões de Projeto Utilizados

# Factory Method

Descrição:  
O padrão Factory Method foi empregado para criar objetos específicos com base no tipo de arquivo JSON sendo lido. No caso deste projeto, o `JsonParserFactory` foi implementado para retornar um parser apropriado de acordo com o nome do arquivo. Isso torna o sistema flexível e facilmente extensível para lidar com diferentes tipos de arquivos JSON no futuro.

Justificativa:  
O Factory Method facilita a extensão do sistema para novos formatos de arquivos sem a necessidade de modificar o código existente, alinhando-se com o Princípio Aberto/Fechado (Open/Closed Principle - OCP).

# Adapter

Descrição:  
O padrão Adapter foi utilizado para transformar os dados das cidades, lidos do arquivo JSON, em um formato adequado para um relatório HTML. O `HtmlAdapter` recebe uma lista de cidades e gera um conteúdo HTML formatado.

Justificativa:  
O Adapter permite que classes com interfaces incompatíveis trabalhem juntas, convertendo a interface de uma classe para outra que o cliente espera. Isso facilita a reutilização do código de geração de relatórios em diferentes formatos de saída (como HTML e TXT).

# Observer

Descrição:  
O padrão Observer foi adotado para permitir que diferentes partes do sistema sejam notificadas quando um relatório é gerado. A classe `ReportSubject` é responsável pela geração do relatório e pela notificação dos observadores, como o `LoggerObserver`.

Justificativa:  
O Observer promove um sistema desacoplado, permitindo que diversas partes do código reajam a eventos (como a geração de um relatório) sem precisar de uma conexão direta. Isso cumpre o Princípio da Responsabilidade Única (Single Responsibility Principle - SRP), separando a lógica de notificação da lógica de geração de relatórios.

 ## 2. Refatorações Baseadas nos Princípios SOLID

# 2.1 Princípio da Responsabilidade Única (SRP)

Refatoração:  
Cada classe foi refatorada para ter uma única responsabilidade. Por exemplo, o `HtmlAdapter` é responsável apenas por converter dados em formato HTML, enquanto a classe `ReportSubject` lida com a geração do relatório e a notificação dos observadores.

Justificativa:  
Isso mantém o código organizado e fácil de manter, pois cada classe possui uma responsabilidade bem definida.

# 2.2 Princípio Aberto/Fechado (OCP)

Refatoração:  
O `JsonParserFactory` foi implementado para permitir a criação de diferentes parsers para diversos tipos de arquivos sem modificar a estrutura existente. Para adicionar suporte a novos tipos de arquivos, basta criar um novo parser e registrá-lo na fábrica.

Justificativa:  
Isso assegura que o código seja aberto para extensão, mas fechado para modificação, facilitando a adição de novas funcionalidades sem quebrar o código existente.

# 2.3 Princípio da Inversão de Dependência (DIP)

Refatoração:  
As classes que utilizam parsers e adapters não dependem de implementações concretas, mas sim de abstrações. Isso foi alcançado por meio do uso de interfaces e classes abstratas.

Justificativa:  
Isso facilita a substituição de implementações concretas sem alterar as classes que delas dependem, promovendo um design mais flexível e testável.

 ## 3. Explicação do Script de Teste

# 3.1 Finalidade do Script de Teste

O script de teste foi criado para validar se as funcionalidades principais do sistema estão operando conforme esperado. Ele verifica se:

- O parser adequado é criado pelo `JsonParserFactory`.
- O `HtmlAdapter` gera um relatório HTML com as cidades.
- O padrão Observer notifica corretamente os observadores quando um relatório é gerado.

# 3.2 Como Executar os Testes

Para executar os testes, certifique-se de ter o **Node.js** instalado no seu ambiente. Em seguida, use o seguinte comando no terminal, a partir do diretório raiz do projeto: **npx jest**.
