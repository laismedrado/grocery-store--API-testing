### grocery-store-API-testing

---

   Este projeto de teste automatizado utiliza o Postman para testar uma API existente. A integração do Newman com o pipeline do Jenkins facilita a execução automatizada   
   dos testes e desempenha um papel fundamental ao fornecer relatórios detalhados dos resultados, tornando o processo de análise mais eficiente. Além disso, qualquer 
   modificação feita neste repositório aciona automaticamente a pipeline no Jenkins, garantindo que os testes sejam executados de forma contínua e automatizada, 
   contribuindo para a manutenção da qualidade do software.

  ## Tecnologias utilizadas
  
    - Postman 
    - node version v18.16.1
    - newman v5.3.2
    - newman-reporter-html
    - Jenkins
    - Docker
    - Ngrok

  ## Documentação:

   [Consulte Documentação](https://github.com/vdespa/Postman-Complete-Guide-API-Testing/blob/main/simple-grocery-store-api.md)

  ## Configurando o ambiente de teste

### Pré-requisitos:

Certifique-se de ter o Docker instalado e em execução em sua máquina. Você pode baixar e instalar o Docker a partir do [site oficial do Docker](https://www.docker.com/get-started).

### Passos:

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
:bulb: **Observação:** Este comando iniciará o contêiner Docker com o Jenkins em execução. para acessar o Jenkins através do navegador  é necessário utilizar aURL do NGROK.

4. **Instalação inicial do Jenkins:**
 
```bash
Siga as instruções na página inicial do Jenkins para concluir a instalação inicial.
```
5. **Configuração da Pipeline:**
   
```bash
- Após a instalação inicial, crie uma pipeline para hospedar o projeto no GitHub seguindo estas etapas:
- Clique em "Novo Item" no Jenkins.
- Selecione "Pipeline" e configure os detalhes do projeto.
- Certifique-se de fornecer o caminho correto para o arquivo pipeline.jenkinsfile, que contém o script para executar os testes do Postman na pipeline.
```
6. **Configuração do Webhook no GitHub:**

```bash
- Configure um webhook no GitHub para acionar automaticamente a execução da pipeline no jenkins sempre que houver alterações no repositório na branch principal.
- Configure o webhook com a URL fornecida pelo Ngrok para permitir acesso externo a outros serviços.
```

### Report

O arquivo HTML com o resultado dos testes é gerado usando o Newman e o Htmlextra. Para acessar este relatório na página da pipeline do projeto, siga estas etapas:
```bash
1. Na página da pipeline do projeto no Jenkins, localize e clique na etapa ou estágio onde os testes foram executados.
2. Dentro da etapa ou estágio, você há uma seção chamada "Newman".
3. Clique na opção "Newman" para expandir as opções disponíveis.
4. Haverá na parte superior direita da tela um  link para baixar um arquivo zipado que contém os resultados dos testes.
5. Baixe e extraia o arquivo zipado. Nele, estará o arquivo XML e o arquivo HTML extra do relatório dos testes.
```
:bulb: Isso permitirá o acesso e analise dos resultados dos testes executados durante a pipeline diretamente do Jenkins.

### Os testes automatizados

Os testes automatizados realizados nesta API abrangem operações CRUD (Create, Read, Update, Delete), verificam códigos de status das respostas, garantem autenticação correta, validam entradas e detectam erros. Esses testes são essenciais para assegurar o funcionamento adequado da API em diferentes cenários e manter a integridade e segurança das operações realizadas.

### Resumo dos testes

- **Operações CRUD**: Foram testadas as operações CRUD para garantir que os endpoints correspondentes estejam funcionando corretamente.
- **Verificação de códigos de status**: Os testes incluem verificações dos códigos de status das respostas para garantir que estejam de acordo com as expectativas da documentação .
- **Autenticação correta**: A autenticação é validada para garantir que apenas usuários autorizados possam acessar os recursos protegidos pela API.
- **Validação de entradas**: As entradas fornecidas aos endpoints da API são validadas para garantir que estejam corretas e consistentes.
- **Detecção de erros**: Testes específicos foram desenvolvidos para detectar e lidar com possíveis erros que possam ocorrer durante as interações com a API.

### Resultados

Os testes automatizados confirmaram a conformidade da API com as expectativas, assegurando a integridade e segurança das operações realizadas. Entretanto, foram identificados dois erros que necessitam de atenção especial, ambos relacionados ao endpoint "Get all products - result = 0":

- **erro 01** 

<div style="display: flex; justify-content: space-between;">
      <img src="https://github.com/laismedrado/simple-grocery-store-api/assets/31759644/8bf1a12b-f2f0-493e-80b7-5c5a9deb3bf5" style="width:80%;" alt="Imagem 2">
</div>

---
Ao enviar o parâmetro "result" com o valor 0 no endpoint "Get all products", contrariando as especificações da API, a resposta esperada era um código de status 400 (Bad Request). No entanto, a API retornou um status 200 (OK), indicando uma falha na validação dos parâmetros de entrada.

- **erro 02**

<div style="display: flex; justify-content: space-between;">
<img src="https://github.com/laismedrado/simple-grocery-store-api/assets/31759644/01b41544-2f28-49e4-a496-78e6c1f9cd06" style="width: 80%;" alt="Imagem 1">
</div>

---
Além disso, a mensagem de erro recebida não correspondeu àquela esperada de acordo com a documentação. Esta diferença sugere uma possível inconsistência entre a implementação real e a especificação da API, o que pode comprometer a experiência do usuário e a integridade dos dados.





## Entre em contato
email: laismedrado@live.com
redes socias: https://www.linkedin.com/in/lais-medrado/


