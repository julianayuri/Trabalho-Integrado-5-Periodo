# TRABALHO INTEGRADO: Título do trabalho

Trabalho desenvolvido durante as disciplinas de:
- Banco de Dados 2, 
- Engenharia de Software, 
- Programação Orientada a Objetos 2,
- Projeto de Sistemas


**INTEGRANTES DO GRUPO:** 
- André Barbosa da Vitoria<br>
- Juliana Yuri Kanezaki de Souza<br>

        
#Sumário


#Gerência de Requisitos

##1	Motivação e Propósito do Sistema 
A Moulin Surf School é uma escola de surf que possui uma cantina, atualmente não existe um controle automatizado do fluxo de caixa, provocando lacunas nas informações de entrada de caixa. O cliente deseja um sistema que auxilie no controle do fluxo de caixa e que fornece estatísticas das vendas efetuadas.

##2	Personas
descrever os personas de tal forma que descreva as necessidades do usuário pelo sistema.

##3	Minimundo 
A Moulin surf school deseja uma sistema de informação para gerenciar a cantina da escola. 
O sistema deve permitir que o vendedor cadastre, visualize, altere e remova os produtos do banco de dados. Os produtos vendidos são divididos em categorias como: bebidas, lanches e gelados. Sobre os produtos deseja-se saber: preço de custo, preço de venda, fornecedor e categoria. Cada alimento tem seu próprio preço. A escola deseja registrar o fluxo de caixa da cantina. Sobre a venda deseja-se saber: vendedor, produtos, preço total, data e horário.  O sistema deve apresentar relatório de venda de produtos com valor, descrição dos produtos, data e nome do vendedor. 

##4	Requisitos de Usuários
###4.1	Requisitos Funcionais (Histórias de Usuário)

| ID | Descrição | Prioridade | Pontos |
| --- | --- | --- | --- |
| RF01 | Eu, como vendedor, quero fazer o controle de vendas pelo celular para que eu tenha maior mobilidade.  | Should | 2 |
| RF02 | Eu, como administrador, desejo saber o fluxo de caixa de determinado período | Must | 3 |
| RF04 | Eu, como administrador, desejo ter acesso à relatórios sobre produtos mais vendidos | Must |  |
| RF03 | Eu, como vendedor, desejo um sistema que calcule o preço total da venda e o troco do cliente para maior agilidade na venda. | Must |  | 

###4.2	Requisitos Não Funcionais

| ID | Descrição | Prioridade | Categoria | Escopo |
| --- | --- | --- | --- | --- |
| RNF01 | Deve ser possível utilizar o sistema mesmo sem conexão com a internet | Must |  Acessibilidade | Funcionalidade |
| RNF02 |A entrada de dados para efetuar o cadastro de um produto deverá ser realizada em no máximo 30 segundos | Should | Facilidade de Operação | Funcionalidade |
| RNF03 |O tempo de resposta de cadastro deve ser de no máximo de 3 segundos | Should | Eficiência de Tempo | Funcionalidade |
| RNF04 | O sistema deve registrar o nome do vendedor em cada venda | Must| Não Repúdio| Funcionalidade |
| RNF05 | O sistema deve apresentar o valor total da venda em no máximo 0,5 segundos | Should | Eficincia de Tempo | Funcionalidade |
| RNF06 | O sistema deve ser capaz de armazenar o histórico dos preços dos produtos | Must | Não Repúdio| Funcionalidade |
| RNF07 |O sistema deve ser capaz de operar em múltiplas plataformas (Android, Windows) | Should | Adaptabilidade | Funcionalidade |
| RNF08 | O sistema deve controlar o acesso às funcionalidades. Funcionalidades de atendimento a clientes devem ser restritas a vendedores. Funcionalidades de controle de caixa devem ser restritas a administradores.  | Must | Segurança de Acesso | Sistema|

###4.3	Regras de Negócio

| ID | Descrição | Prioridade | 
| --- | --- | --- |
| RN01 | Uma reserva expira quando passadas mais do que 24h de sua comunicação para o cliente. | Must |
| RN02 | Clientes em atraso não podem efetuar nem locações nem reservas. | Should |


#Desenvolvimento do Sistema
##1.    Análise de Sistemas:
###1.1  Subsistemas
inserir diagrama dos subsistemas UML
###1.2  Modelagem de Casos de uso 
inserir diagramas dos Casos de Uso (UML) e descrever brevemente.

###1.3  Modelagem Estrutural (Modelo Conceitual)
** ATENÇO: USAR Notação Entidade-Relacionamentos se estiver fazendo BD2 e o diagrama de classes se estiver fazendo Projeto de Sistemas**
![Alt text](https://github.com/andrebvitoria/Trabalho-Integrado-5-Periodo/blob/master/Modelos/Modelo%20Conceitual%20-%20Moulin.jpg?raw=true "Modelo Conceitual")
###1.4  Modelagem Comportamental
inserir principais diagramas comportamentais da análise (principalmente, estados)
###1.5  Dicionário de Dados
[classe/entidade]: [descrição da classe]
    
    EXEMPLO:
    CLIENTE: classe/entidade que representa as informações relativas ao cliente<br>
    CPF: atributo que representa o número de Cadastro de Pessoa Física para cada cliente da empresa.<br>
    
##2.    Projeto de Sistemas:
###2.1  Projeto Arquitetural 
####2.1.1   Plataforma de Implementação e Tecnologias
O sistema em questão trata-se de um Sistema de Informação e apresenta as seguintes características: <br>
- Há apenas um computador desktop para a escola inteira, portanto o sistema deve estar disponível também em plataforma mobile;
- O sistema envolve um grande fluxo de dados e a sua gerência deve ser feita usando um banco de dados;
- Está integrado com outros sistemas em um mesmo banco de dados; <br><br>
Levando-se em consideração essas características, decidiu-se implementar o sistema para a Cantina da escola usando as linguagens de programação PHP e NodeJS e linguagens de desenvolvimento web (HTML5, JavaScript e CSS3), o banco de dados relacional PostgreSQL e o framework de desenvolvimento para múltiplas plataformas Ionic .

####2.1.2   Atributos de Qualidade e Táticas
 CATEGORIAS | RNF'S | TÁTICAS | 
| --- | --- | --- |
| Facilidade de Operação | RNF02| Prover ao usuário a capacidade de entrar com comandos que permitam operar o sistema de modo mais eficiente. Para tal, as interfaces do sistema devem permitir, sempre que possível, a entrada por meio de seleção ao invés da digitação de campos. | 
| Não Repúdio | RNF04 | O sistema gerará logs de evento, portanto sempre que um vendedor realizar uma venda será gerado um log armazenando o autor do evento.| 
| Segurança de Acesso | RNF08| Identificar usuários usando login e autenticá-los por meio de senha.<br>Autorizar usuários, criando os seguintes grupos: (i) Vendedor – acesso às funcionalidades do controle de vendas e CRUD (Criar, Ler, Atualizar, Deletar) de produtos; (ii) Administrador – Todas as funcionalidades do Vendedor e visualização de estatísticas de vendas. | 


####2.1.3   Arquitetura de Software
apresentar diagrama UML da arquitetura do sistema. justificar as decisões tomadas.

###2.2. Projeto Detalhado
OBS: repetir as seções abaixo para cada subsistema
####2.2.1.   Projeto da Lógica de Negócio
#####Projeto do Domínio
apresentar diagrama de classes do domínio
#####Projeto da Aplicação
apresentar diagramas de sequência e mapeamento dos casos de uso para classes
####2.2.2.  Projeto da Interface com Usuário
#####Projeto da Visão
apresentar protótipos de telas e diagramas de classes UML (caso realizado)
OBS: Essa visão não tem nada a ver com Views de Banco de Dados

__OBS DE BD2__: neste ponto a codificação não e necessária, somente as ideias de telas devem ser criadas, o princípio aqui é pensar na criação da interface para identificar possíveis informações a serem armazenadas ou descartadas <br>

Sugestão: https://balsamiq.com/products/mockups/<br>

![Alt text](https://github.com/discipbd2/topicos-trabalho/blob/master/balsamiq.png?raw=true "Title")
#####Projeto da Interação Humana
apresentar diagrama de classes da IU com controladores e diagrama de sequências. Apresentar diagrama com estados de navegação.
####2.2.3.  Projeto da Persistência de Dados
apresentar classes de acesso ao banco de dados. apresentar diagramas de sequência.

####2.4.   Padrões
#####Padrões Arquiteturais
#####Padrões de Projeto

No diagrama abaixo é destacado o padrão de projeto método fábrica que foi utilizado para melhorar a coesão e diminiuir o acoplamento entre as clases do sistema. O pode-se notar a classe FabricaDeFormatos cria os objetos FormatoPng, FormatoJpeg e FormatoGif tirando a dependencia entre a classes Main e essas classes. Vale ressaltar que o padrão utiliza um Interface Formato para diminiuir o acoplamento entre as classes.

![Alt text](https://github.com/felipefo/poo2/blob/master/Padroes_de_Projeto/Cria%C3%A7%C3%A3o/metodo_fabrica/ImagemMetodoFabrica/padrao_metodo_fabrica_conversao_imagem.png)


O padrão foi utilizado para resolver o problema de .....

O padrão foi utilizado para resolver o problema de .....


##3.    Banco de Dados (BD)


###3.1 Decisões do Projeto 
    [atributo]: [descrição da decisão]
    
    EXEMPLO:
    a) Campo endereço: em nosso projeto optamos por um campo multivalorado e composto, pois a empresa 
    pode possuir para cada departamento mais de uma localização... 
    b) justifique!


###3.2	Modelo Lógico<br>
###3.3	MODELO FÍSICO<br>
###3.4	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
####3.4.1 DETALHAMENTO DAS INFORMAÇÕES
        Detalhamento sobre as informações e processo de obtenção ou geração dos dados.
        Referenciar todas as fontes referentes a:
        a) obtenção dos dados
        b) obtenção de códigos reutilizados
        c) fontes de estudo para desenvolvimento do projeto
        
####3.4.2 INCLUSÃO DO SCRIPT PARA CRIAÇÃO DE TABELAS E INSERÇÃO DOS DADOS (ARQUIVO ÚNICO COM):
        a) inclusão das instruções para criação das tabelas e estruturas de amazenamento do BD
        b) inclusão das instruções de inserção dos dados nas referidas tabelas
        c) inclusão das instruções para execução de outros procedimentos necessários

###3.5	TABELAS E PRINCIPAIS CONSULTAS<br>
####3.5.1	GERACAO DE DADOS (MÍNIMO DE 1,5 MILHÃO DE REGISTROS PARA PRINCIPAL RELAÇAO)<br>
    Data de Entrega: (Data a ser definida)
<br>
OBS: Incluir para os tópicos 9.2 e 9.3 as instruções SQL + imagens (print da tela) mostrando os resultados.<br>

####3.5.2	SELECT DAS TABELAS COM PRIMEIROS 10 REGISTROS INSERIDOS<br> 
    Data de Entrega: (Data a ser definida)
<br>
####3.5.3	SELECT DAS VISÕES COM PRIMEIROS 10 REGISTROS DA VIEW<br>
        a) Descrição da view sobre que grupos de usuários (operacional/estratégico) <br>
        e necessidade ela contempla.
        b) Descrição das permissões de acesso e usuários correlacionados (após definição <br>
        destas características)
    Data de Entrega: (Data a ser definida)
<br>
####3.5.4	LISTA DE CODIGOS DAS FUNÇÕES, ASSERÇOES E TRIGGERS<br>
        Detalhamento sobre funcionalidade de cada código.
        a) Objetivo
        b) Código do objeto (função/trigger/asserção)
        c) exemplo de dados para aplicação
        d) resultados em forma de tabela/imagem
<br>
####3.5.5	Administração do banco de dados<br>
        Descrição detalhada sobre como serão executadas no banco de dados as <br>
        seguintes atividades.
        a) Segurança e autorização de acesso:
        b) Estimativas de aquisição de recursos para armazenamento e processamento da informação
        c) Planejamento de rotinas de manutenção e monitoramento do banco
        d) Plano com frequencia de análises visando otimização de performance
<br>
####3.5.6	Backup do Banco de Dados<br>
        Detalhamento do backup.
        a) Tempo
        b) Tamanho
        c) Teste de restauração (backup)
        d) Tempo para restauração
        e) Teste de restauração (script sql)
        f) Tempo para restauração (script sql)
<br>

####3.5.7	APLICAÇAO DE ÍNDICES E TESTES DE PERFORMANCE<br>
    a) Lista de índices, tipos de índices com explicação de porque foram implementados
    b) Performance esperada VS Resultados obtidos
    c) Tabela de resultados comparando velocidades antes e depois da aplicação dos índices.
<br>
    Data de Entrega: (Data a ser definida)
<br>   
####3.5.8	ANÁLISE DOS DADOS COM ORANGE<br>    
    a) aplicação de algoritmos e interpretação dos resultados
<br>
    Data de Entrega: (Data a ser definida)
<br>
###3.6	ATUALIZAÇÃO DA DOCUMENTAÇÃO/ SLIDES E ENTREGA FINAL<br>
<br>
    Data de Entrega: (Data a ser definida)
<br>
###3.7	DIFICULDADES ENCONTRADAS PELO GRUPO<br>  




#Gestão de Configuração
##1.    Metodologia
descrever metodologias e políticas que serão usadas para realizar a gestão de configuração como, por exemplo, Gitflow, rastreabilidade de requisitos e mudanças. É necessário descrever em detalhes os procedimentos.
##2.    Arquitetura
descrever ferramentas e a integração dessas para a arquitetura. 
##3.    Integração Contínua e Delivery Contínua
Descrever como será aplicado esses conceitos.

#Gestão de Projetos
##1.    Project Model Canvas (PMC)
Visão geral do projeto.
##2.    Cronograma macro de sprints 
datas dos sprints.
##3.    Backlog de histórias de Usuário 
lista de histórias de usuário categorizadas, priorizadas e com o esforço. A categorização deve utilizar a técnica MoSCoW. 
Acompanhamento do projeto: o grupo deve apresentar histórico, por sprint,  do acompanhamento do projeto da seguinte forma:
- Apresentando o Burndown do projeto.
- Apresentando a velocidade do time.
- Modificações do backlog.
##4.    Burn down dos sprints
acompanhamento dos sprints. Cada Sprint deve ter uma seção descrevendo o que foi realizado e o planejado (por meio do  o gráfico e Burndown do Sprint).
##5.    Retrospectiva 
Apresentar a retrospectiva da equipe do sprint realizado.

#Gerência de Qualidade
##1.    Métricas de qualidade 
definir métricas de qualidade para cada artefato do projeto como, por exemplo, quantidade de codesmell, complexidade ciclomática e outras. 
##2.    Classes de equivalência e particionamento de equivalência 
defina as classes de equivalências para as métricas de qualidade. 

##3.    Medição 
seção que escreve como as métricas estão sendo atingidas. Essa seção deve ser atualizada por sprint. 
##4.    Testes
Técnicas utilizadas para os testes: apresentar as técnicas utilizadas para o planejamento e execução de testes como, por exemplo, teste funcional sistemático e testes estruturais. 
##5.    Cenário de Teste
apresentar todos os cenários de teste sucesso e falhas das histórias de usuário.  
##6.    Histórico  
O grupo deve apresentar a evolução da qualidade dos itens ao longo das entregas, ou seja, em outras palavras, o grupo deve apresentar o histórico de evolução da qualidade dos artefatos de software e discursar o motivo da evolução.

#Diário de Bordo

o grupo deve apresentar semanalmente um relato da atividade do grupo. O relato pode conter qualquer tipo de informação (fotos, vídeos) que possam auxiliar no entendimento das atividades do grupo. 

OBS: organize o diário para que não se misture com a documentação. de preferência, coloque-o em outra página.

**FORMATACAO NO GIT:** https://help.github.com/articles/basic-writing-and-formatting-syntax/
