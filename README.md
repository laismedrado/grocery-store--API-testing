# grocery-store-API-testing

The automated testing project utilizes Postman to test an existing API, with Newman integrated into the Jenkins pipeline, facilitating automated test execution. 
## O que é
This repository contains API tests for a simplified grocery shopping system, conducted using the Postman tool. It provides details on the tests performed, including the tested endpoints, implemented test cases, and obtained results. The tests cover a variety of operations, such as viewing products, adding items to the cart, placing orders, and other interactions with the API. These te help ensure the correct functionality and integrity of the API endpoints, providing comprehensive validation of the features offered by the shopping system.
## Tecnologias utilizadas
- Postman 
- node version v18.16.1
- newman v5.3.2
- newman-reporter-html
- Jenkins
- Docker
- Ngrok
  
## Documentações
- [Consulte Documentação](https://github.com/vdespa/Postman-Complete-Guide-API-Testing/blob/main/simple-grocery-store-api.md)

## Configurando o ambiente do Jenkins para executar a pipeline de testes automatizados do repositório do GitHub

## Pré-requisitos

Certifique-se de ter o Docker instalado e em execução em sua máquina. Você pode baixar e instalar o Docker a partir do [site oficial do Docker](https://www.docker.com/get-started).

## Passos testestetstes

1. Clone este repositório em sua máquina local:

    ```bash
    git clone https://github.com/laismedrado/grocery-store-API-testing.git
    ```

2. Navegue até o diretório do repositório clonado:

    ```bash
    cd simple-grocery-store-api

    ```

3. Execute o seguinte comando para iniciar o contêiner do Jenkins com suporte ao plugin do Postman:

    ```bash
    docker run -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home --env JAVA_OPTS="-Dfile.encoding=UTF8" vdespa/jenkins-postman
    ```

Este comando iniciará o contêiner Docker com o Jenkins em execução. Você pode acessar o Jenkins através do navegador, digitando a URL do NGROK

4. **Instalação inicial do Jenkins:**
   - Siga as instruções na página inicial do Jenkins para concluir a instalação inicial.

5. **Configuração da Pipeline:**
   - Após a instalação inicial, crie uma pipeline para hospedar o projeto no GitHub seguindo estas etapas:
     - Clique em "Novo Item" no Jenkins.
     - Selecione "Pipeline" e configure os detalhes do projeto.
     - Certifique-se de fornecer o caminho correto para o arquivo pipeline.jenkinsfile, que contém o script para executar os testes do Postman na pipeline.

6. **Configuração do Webhook no GitHub:**
   - Configure um webhook no GitHub para acionar automaticamente a execução da pipeline no jenkins sempre que houver alterações no repositório na branch principal.
   - Configure o webhook com a URL fornecida pelo Ngrok para permitir acesso externo a outros serviços.


### Report

O arquivo HTML com o resultado dos testes é gerado usando o Newman e o Htmlextra. Para acessar este relatório na página da pipeline do projeto, siga estas etapas:

1. Na página da pipeline do projeto no Jenkins, localize e clique na etapa ou estágio onde os testes foram executados.
2. Dentro da etapa ou estágio, você há uma seção chamada "Newman".
3. Clique na opção "Newman" para expandir as opções disponíveis.
4. Haverá na parte superior direita da tela um  link para baixar um arquivo zipado que contém os resultados dos testes.
5. Baixe e extraia o arquivo zipado. Nele, estará o arquivo XML e o arquivo HTML extra do relatório dos testes.

Isso permitirá o acesso e analise dos resultados dos testes executados durante a pipeline diretamente do Jenkins.

## Resultados dos Testes Automatizados

Os testes automatizados realizados nesta API abrangem operações CRUD (Create, Read, Update, Delete), verificam códigos de status das respostas, garantem autenticação correta, validam entradas e detectam erros. Esses testes são essenciais para assegurar o funcionamento adequado da API em diferentes cenários e manter a integridade e segurança das operações realizadas.

### Resumo dos Testes

- **Operações CRUD**: Foram testadas todas as operações CRUD para garantir que os endpoints correspondentes estejam funcionando corretamente.
- **Verificação de Códigos de Status**: Os testes incluem verificações dos códigos de status das respostas para garantir que estejam de acordo com as expectativas.
- **Autenticação Correta**: A autenticação é validada para garantir que apenas usuários autorizados possam acessar os recursos protegidos pela API.
- **Validação de Entradas**: As entradas fornecidas aos endpoints da API são validadas para garantir que estejam corretas e consistentes.
- **Detecção de Erros**: Testes específicos foram desenvolvidos para detectar e lidar com possíveis erros que possam ocorrer durante as interações com a API.

### Resultados

Os resultados dos testes automatizados demonstraram que a API responde conforme o esperado, mantendo a integridade e segurança das operações realizadas. A cobertura abrangente dos testes garante a confiabilidade e robustez da API em diferentes cenários de uso.

erro 01 :

![image](https://github.com/laismedrado/simple-grocery-store-api/assets/31759644/8bf1a12b-f2f0-493e-80b7-5c5a9deb3bf5)

O parâmetro passado é o 0, o que de acordo com a documentação não é aceito; e ao em vez de retornar um código de status 400 (Bad Request) como esperado, foi  retornado o status 200 (OK);

 erro 02

 ![image](https://github.com/laismedrado/simple-grocery-store-api/assets/31759644/01b41544-2f28-49e4-a496-78e6c1f9cd06)

Este teste está comparando o retorno esperado com o recebido de acordo com oque tem descrito na documentação; e percebe-se que
não é a mensagem de retorno correta logo , esse teste també está falhando;



## Entre em contato
email: laismedrado@live.com
redes socias: https://www.linkedin.com/in/lais-medrado/


