# Azure na Prática
Detalhamento do Trabalho executado com a Machine Learning na Prática no Azure ML

## Criação de Conta no Portal da Azure

1º Acesse o site: https://azure.microsoft.com;
2º Clique em Conta Gratuita;
3º Preencha seus dados pessoais e de cartão de crédito (Onde será cobrado um valor simbolico de 1,00$ para validação do cartão;
4º Confirmar E-mail de para ativação do cadastro.

## Criação do Workspace na Azure Machine Learning

1º Após a criação da conta e acessar a sua conta no Portal Azure, pesquise na barra "Pesquisar recursos, serviços e documentos (G+/)", Azure Machine Learning;

2º Ao clicar em Criar Azure Machine Learning ele irá lhe direcionar, para o campo de criação de Workspace do Machine Learning, onde voçê deve preencher os campos da seguinte forma:
      Assinatura: Azure Substcription 1 (caso apareça outro tipo de assinatura, não a necessidade de se alterar, as assinaturas variam de acordo com o seu cadastro no Portal da Azure);
        Grupo de recursos: (Clicar em Criar um novo, e criar com o nome que voçê desejar. Será nesse grupo de recursos, onde voçê irá executar os trabalhos);

      Workspace details (Área de configuração básica do seu local de trabalho);
        Nome: (nome do seu local de trabalho, preencha coloque o nome que voçê preferir);
        Região: (nesse campo voçê seleciona o local do servidor a ser utilizado, esse local influencia na taxa a ser cobrada pela utilização dos recursos e na velocidade do processamento das ações);
        Storage Account: (será criado um nome aleatório, não há necessidade de se alterar)(É o nome do repositório dos nossos HD's);
        Key vault: (será criado uma Key aleatória, não há necessidade de se alterar) (Será o repositório responsável por armazenar nossos segredos, chaves, certificados e etc...);
        Application insights: (será criado uma nome aleatória, não há necessidade de se alterar);
        Container registry: (para o laboratório de teste, não há a necessidade de registrar um container);

        3º Há também outros complementos na criação da nossa Azure Machine Learning, que se encontram nas abas, Networking(onde voçê define se o Workspace é publico, privado via internet ou privado com acesso aprovado), Encryption(define se é uma chave gerenciada pela Microsoft, ou pela empresa), Identity(onde será preenchido as permições de acesso e etc..), Tags(rotulos para adicionar em recursos, facilitando a rastreabilidade dos mesmos e o controle de custos), Review + create(aba de revisão antes da criação do recurso).

        ## Usando o aprendizado de máquina automatizado para treinar com um modelo da Microsoft Azure.

        1º Após a criação do Workspace, clicar em "Go to resource". (voçê será redirecionado para o Azure Machine Learning Studio, onde voçê realizará os trabalhos);
        
        2º Clicar em "Launch studio", onde voçê será redirecionado para a página "https://ml.azure.com". Talvez ao acessar o Estúdio pela primeira vez, sejá solicitado a criação de um workspace. Este é o Estúdio criado para a execução dos nossos trabalhos e onde terá alguns catálogos de modelos e outros recursos úteis, para a criação dos nossos trabalhos;

        3º Na página "Diretório Padrão"(página home do Estúdio), estará localizados os seus workspaces, Componentes de aprendizado, Tutoriais e Recursos adicionais. Selecione seu workspace;

        4º Na página do seu workspace, no canto direito, clicar em ML automatizado. Nessa página clicar em "Novo trabalho de ML autorizado", isso irá abrir uma janela para a criação do seu trabalho de ML automatizado;

        5º Preencha os campos de acordo com o passo a passo descrito no site "https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html", da mesma forma que a baixo:
        
             Configurações básicas :

                Nome do trabalho : mslearn-bike-automl;
                Novo nome do experimento : mslearn-bike-rental;
                Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas;
                Marcadores : nenhum.
                
             Tipo de tarefa e dados :

                Selecione o tipo de tarefa : Regressão;
                Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:
                   Tipo de dados :
                    Nome : aluguel de bicicletas;
                    Descrição : dados históricos de aluguel de bicicletas;
                    Tipo : Tabular;
              Fonte de dados :
                Selecione Dos arquivos da web;
                  URL da Web :
                    URL da Web :https://aka.ms/bike-rentals;
                    Ignorar validação de dados : não selecionar.
              Configurações :
                Formato de arquivo : Delimitado;
                Delimitador : Vírgula;
                Codificação : UTF-8;
                Cabeçalhos de coluna : apenas o primeiro arquivo possui cabeçalhos;
                Pular linhas : Nenhum;
                O conjunto de dados contém dados multilinhas : não selecione;
              Esquema :
                Incluir todas as colunas exceto Path;
                Revise os tipos detectados automaticamente;
                Selecione Criar . Após a criação do conjunto de dados, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

             Configurações de tarefa :

              Tipo de tarefa : Regressão;
              Conjunto de dados : aluguel de bicicletas;
              Coluna de destino : Aluguéis (inteiro);
              Configurações adicionais :
                Métrica primária : raiz do erro quadrático médio normalizado;
                Explique o melhor modelo : Não selecionado;
                Usar todos os modelos suportados : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
                Modelos permitidos : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo                         necessário para executar o trabalho.
              Limites : expanda esta seção;
                Máximo de testes : 3;
                Máximo de testes simultâneos : 3;
                Máximo de nós : 3;
                Limite de pontuação da métrica : 0,085 ( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho                       termina. );
                Tempo limite : 15;
                Tempo limite de iteração : 15;
                Habilitar rescisão antecipada : selecionado.
              Validação e teste :
                Tipo de validação : divisão de validação de trem;
                Porcentagem de dados de validação : 10;
                Conjunto de dados de teste : Nenhum.

             Calcular :

              Selecione o tipo de computação : sem servidor;
              Tipo de máquina virtual : CPU;
              Camada de máquina virtual : Dedicada;
              Tamanho da máquina virtual : Standard_DS3_V2*;
              Número de instâncias : 1.
        * Se a sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.

          Envie o trabalho de treinamento. Ele inicia automaticamente.

          Espere o trabalho terminar. Pode demorar um pouco.
        
    ## Avaliando e Testando o Modelo Criado.

        1º Após a validação do trabalho criado, clicar no nome do trabalho criado, para ser redirecionado aos dados do trabalho, com todo o histórico do processo de conclusão do trabalho;

        2º Clique no nome de exibição do trabalho, para ser direcionado a Propriedades do trabalho, onde podemos explorar as abas de, Visão geral, Verificadores de integridade dos dados, Modelos + trabalhos filhos, Saídas + logs e trabalho filho;

        3º Agora iremos avaliar as métricas utilizadas no modelo e analisar se está tudo ok para a criação da implementação. Clique no "Nome do algoritimo, para visualizar os detalhes. Na aba "Métricas", observe se os gráficos "residuals" e "predicted_true", estão selecionados, confira se os gráficos estão corretos;

        4º Clique na aba Visão geral, no canto direito da tela, no quadrado "Melhor resumo do modelo", clicar no nome do "Modelos Registrados", isso irá lhe direcionar para a página de modelo responsável pelo seu trabalho;

        5º Nessa página, iremos clicar em "Implantar", selecionar a opção "Serviço Web" e criar a nossa implementação conforme o modelo descrito no site "https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html", da mesma forma que a baixo:

              Preencher os campos como o exemplo abaixo:
                  Nome : prever-alugueis;
                  Descrição : Prever aluguel de bicicletas;
                  Tipo de computação : Instância de Contêiner do Azure;
                  Habilitar autenticação : selecionado;
                  Aguarde o início da implantação – isso pode levar alguns segundos. O status de implantação do endpoint de previsão de aluguel será indicado na parte principal da                         página como Running;
                  Aguarde até que o status da implantação mude para Succeeded . Isso pode levar de 5 a 10 minutos.

        6º Após a implementação chegou a hora de testar os trabalho realizado, para isso temos que ir no canto esquerdo da tela na opção "Pontos de extremidades", clicar no nome que n´s criamos para esse ponto de extremidade. clicar na aba "Testar", copiar o código JSON, do modelo descrito no site "https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html", da mesma forma que a baixo:

        {
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }
 
        7º Substituir o código do campo de teste, com o código copiado do modelo e clicar em testar;

        8º Se aparecer o resultado ao lado do campo de código do teste semelhante a este:

           {
   "Results": [
     444.27799000000000
   ]
 }
 
        9º Teste concluido com sucesso!
