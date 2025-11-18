# 1. Plano de Teste - Tem Agasalho Aqui

## Projeto

**Projeto:** Tem Agasalho Aqui

**Descrição:**
“Tem Agasalho Aqui” é uma plataforma web que conecta doadores de roupas a pontos físicos de coleta cadastrados no sistema, como ONGs, entidades assistenciais e projetos sociais. Além de listar locais próximos ao CEP do doador por meio da API do Google Maps, o site permite que novas instituições se cadastrem como pontos de coleta, informando seus dados, localização e horários de funcionamento. O projeto busca facilitar o acesso à informação, fortalecer a cultura da doação e promover o engajamento social.

---

## Objetivo

Garantir que os *endpoints* do website estão respondendo adequadamente conforme os requisitos funcionais, avaliando:

* Status HTTP (ex: 200 OK)
* Tempo de resposta das requisições
* Comportamento em diferentes cenários de uso (dados inválidos, acessos não autorizados.)
* Explorar e identificar possíveis bugs, falhas e inconsistências antes do lançamento.

---

## Escopo

### Endpoints: Fluxo de Acesso Público

| Página | Link | Acesso |
| :--- | :--- | :--- |
| Home | http://82.25.75.88/ | Público |
| Sobre | http://82.25.75.88/sobre | Público |
| Pontos de Coleta | http://82.25.75.88/pontosdecoleta | Público |
| Cadastro | http://82.25.75.88/cadastro | Público |
| Termos e Condições | http://82.25.75.88/termos | Público |
| Política de Privacidade | http://82.25.75.88/privacidade | Público |
| Administração (Login) | http://82.25.75.88/administracao | Público |

### Endpoints: Fluxo de Páginas Restritas (Administrativo)

| Página | Link | Acesso |
| :--- | :--- | :--- |
| Painel administrativo | http://82.25.75.88/logado | ADM Logado |
| Cadastrar Ponto | http://82.25.75.88/registroponto | ADM Logado |
| Cadastrar administrador | http://82.25.75.88/addadmuser | ADM Logado |
| Alterar Administrador | http://82.25.75.88/alteraradm | ADM Logado |
| Relatório de Pontos de Coleta | http://82.25.75.88/relatorio-pontos | ADM Logado |
| Alterar Ponto de Coleta | http://82.25.75.88/alterarponto | ADM Logado |

---

## 2. Estratégia de Testes

* **Testes Funcionais**

    * Testes de validações dos endpoints
        * Validação dos *endpoints* de acesso (status HTTP)
        * Validação de conteúdo retornado pelas páginas
        * Validação de requisitos
* **Testes de Desempenho**

    * Avaliação do tempo de resposta das requisições

* **Testes Não Funcionais**
    * Testes exploratórios
    * Testes de acesso sem permissão
    * Testes com dados inválidos ou vazios

---

## 3. Ferramentas e Linguagens Utilizadas

| Ferramenta/Linguagem | Uso Principal |
| :--- | :--- |
| **Postman** | Ferramenta de execução e automação de testes |
| **Excel** | Ferramenta para planilhas, organização e registro dos testes |
| **Word** | Ferramenta de texto para documentar relatório de teste |
| **XMind** | Ferramenta para Mapeamento visual do fluxo das páginas |
| **JavaScript** | Usado para scripts e automações de testes |
| **Gherkin** | Linguagem de descrição de comportamento de software |

---

## 4. Critérios de Aceitação

* Todos os *endpoints* devem retornar status de protocolo HTTP esperado.
* Os dados exibidos devem estar corretos e completos.
* Funcionalidades principais devem funcionar conforme esperado, sem erros.
* Avaliação do tempo de resposta das requisições entre **100ms** e **500ms**.

---

## 5. Riscos

* Falhas na validação de dados (entrada inválida).
* Erros de acesso não autorizado na área administrativa.
* Queda de desempenho com acessos simultâneos.

---

## 6. Entregáveis

* Testes automatizados (Postman e scripts com JavaScript).
* Relatório de execução dos testes com resultados (pass/fail).
* Logs detalhados de erros, se houver falhas.

---

## 7. Ambiente de Testes

| Componente | Detalhe |
| :--- | :--- |
| **OS** | Windows 11 Pro |
| **Processador** | Intel CORE I7 with Intel iRISx |
| **RAM** | 16,00 GB (utilizável: 15,42 GB) |
| **Sistema Operacional** | 64 bits, processador baseado em x64 |
| **Armazenamento** | SSD 250 GB |

---

## 8. Casos de Teste (Resumo)

| ID | Funcionalidade | Descrição do Teste | Entrada | Resultado Esperado | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **CT001** | Acesso à Home | Verificar se a página inicial carrega corretamente | `GET http://82.25.75.88/` | Status 200 + conteúdo visível da home | Pass |
| **CT002** | Página Sobre | Verificar se a página "Sobre" carrega normalmente | `GET http://82.25.75.88/sobre` | Status 200 + texto explicativo do projeto | Pass |
| **CT003** | Listar pontos | Verificar se a página de pontos de coleta está acessível | `GET http://82.25.75.88/pontosdecoleta` | Status 200 + lista de pontos cadastrados | Pass |
| **CT004** | Cadastro | Verificar se o formulário de cadastro está acessível | `GET http://82.25.75.88/cadastro` | Status 200 + formulário visível | Pass |
| **CT005** | Termos | Verificar se a página de termos carrega corretamente | `GET http://82.25.75.88/termos` | Status 200 + texto de termos exibido | Pass |
| **CT006** | Privacidade | Verificar se a política de privacidade está acessível | `GET http://82.25.75.88/privacidade` | Status 200 + conteúdo de política exibido | Pass |
| **CT007** | Login Admin | Verificar se o formulário de login está acessível | `GET http://82.25.75.88/administracao` | Status 200 + campos de login visíveis | Pass |
| **CT008** | Painel Admin | Acessar painel somente após login válido | `Post http://82.25.75.88/logado` | Status 200 + dashboard com dados | Pass |
| **CT009** | Cadastro Ponto | Enviar dados válidos para cadastro de ponto de coleta | `POST` com dados completos | Status 200 + ponto aparece na listagem | Pass |
| **CT010** | Cadastrar Admin | Testar criação de novo admin com dados válidos | `POST` com e-mail e senha | Status 200 + confirmação | Pass |
| **CT011** | Alterar Admin | Testar alterar admin com dados válidos | `PUT` com dados validos | Status 200 + confirmação | Pass |
| **CT012** | Relatório | Testar visualização de quantidade de pontos de coleta | `GET` - visualização | Status 200 + confirmação | Pass |
| **CT013** | Alterar Ponto | Testar alterar dados de ponto de coleta | `PUT` - com dados validos | Status 200 + confirmação | Pass |

---

## 9. Casos de Teste em Gherkin

* **✅ CT001 – Acesso à Home**

    ```gherkin
    Funcionalidade: Página Inicial
    Cenário: Acessar a página inicial do site
      Quando eu acesso a URL "[http://82.25.75.88/](http://82.25.75.88/)"
      Então devo receber o status 200
      E devo visualizar o conteúdo da página inicial
    ```

* **✅ CT002 – Página Sobre**

    ```gherkin
    Funcionalidade: Página Sobre
    Cenário: Acessar a página sobre o projeto
      Quando eu acesso a URL "[http://82.25.75.88/sobre](http://82.25.75.88/sobre)"
      Então devo receber o status 200
      E devo visualizar as informações sobre o projeto
    ```

* **✅ CT003 – Mapa dos pontos de coleta**

    ```gherkin
    Funcionalidade: Pontos de Coleta
    Cenário: Acessar a página de pontos de coleta
      Quando eu acesso a URL "[http://82.25.75.88/pontosdecoleta](http://82.25.75.88/pontosdecoleta)"
      Então devo receber o status 200
      E devo visualizar as informações para realizar busca de ponto de coletas
    ```

* **✅ CT004 – Página de Cadastro**

    ```gherkin
    Funcionalidade: Cadastro de novo ponto
    Cenário: Acessar a página de cadastro
      Quando eu acesso a URL "[http://82.25.75.88/cadastro](http://82.25.75.88/cadastro)"
      Então devo receber o status 200
      E devo visualizar o formulário de cadastro
    ```

* **✅ CT005 – Termos e Condições**

    ```gherkin
    Funcionalidade: Termos de Uso
    Cenário: Acessar a página de termos
      Quando eu acesso a URL "[http://82.25.75.88/termos](http://82.25.75.88/termos)"
      Então devo receber o status 200
      E devo visualizar os termos e condições do site
    ```

* **✅ CT006 – Política de Privacidade**

    ```gherkin
    Funcionalidade: Política de Privacidade
    Cenário: Acessar a página de política de privacidade
      Quando eu acesso a URL "[http://82.25.75.88/privacidade](http://82.25.75.88/privacidade)"
      Então devo receber o status 200
      E devo visualizar o conteúdo da política de privacidade
    ```

* **✅ CT007 – Login do Admin**

    ```gherkin
    Funcionalidade: Login do Administrador
    Cenário: Acessar a tela de login do administrador
      Quando eu acesso a URL "[http://82.25.75.88/administracao](http://82.25.75.88/administracao)"
      Então devo receber o status 200
      E devo visualizar os campos de login
    ```

* **✅ CT008 – Painel do Admin (logado)**

    ```gherkin
    Funcionalidade: Painel Administrativo
    Cenário: Acessar o painel do administrador após login
      Dado que eu esteja autenticado como administrador
      Quando eu acesso a URL "[http://82.25.75.88/logado](http://82.25.75.88/logado)"
      Então devo receber o status 200
      E devo visualizar o painel administrativo
    ```

* **✅ CT009 – Cadastro de Ponto (Admin)**

    ```gherkin
    Funcionalidade: Cadastro de ponto de coleta
    Cenário: Cadastrar um novo ponto de coleta com dados válidos
      Dado que eu esteja autenticado como administrador
      Quando eu envio os dados válidos para "[http://82.25.75.88/registroponto](http://82.25.75.88/registroponto)"
      Então devo receber o status 200
      E o novo ponto deve estar disponível na listagem
    ```

* **✅ CT010 – Cadastro de Novo Admin**

    ```gherkin
    Funcionalidade: Cadastro de novo administrador
    Cenário: Cadastrar um novo usuário administrador
      Dado que eu esteja autenticado como administrador
      Quando eu envio dados válidos para "[http://82.25.75.88/addadmuser](http://82.25.75.88/addadmuser)"
      Então devo receber o status 200
      E devo visualizar uma confirmação de cadastro
    ```

* **✅ CT011 – Alterar Administrador**

    ```gherkin
    Funcionalidade: Alterar administrador com dados válidos
    Cenário: Tentar acessar área restrita sem login
      Quando eu acesso a URL "[http://82.25.75.88/logado](http://82.25.75.88/logado)" com autenticação
      Então devo ser redirecionado e receber status 200
    ```

* **✅ CT012 – Cadastro com dados válidos**

    ```gherkin
    Funcionalidade: Validação de formulário
    Cenário: Enviar formulário de cadastro com dados válidos
      Quando eu envio o formulário com dados válidos para a URL [http://82.25.75.88/alteraradm](http://82.25.75.88/alteraradm)
      Então devo visualizar mensagens de cadastro realizado com sucesso
    ```

* **✅ CT013 – Alterar Ponto de Coleta**

    ```gherkin
    Funcionalidade: Alterar dados de ponto de coleta
    Cenário: Alterar formulário de cadastro com dados válidos
      Quando eu envio o formulário com campos obrigatórios validos para a URL [http://82.25.75.88/alterarponto](http://82.25.75.88/alterarponto)
      Então devo visualizar mensagens de cadastro alterado com sucesso
    ```

---

## 10. Matriz de Risco

| ID | Risco | Probabilidade | Impacto | Ação Preventiva / Mitigação |
| :--- | :--- | :--- | :--- | :--- |
| **R1** | Endpoint não responder (erro 404 ou 500) | Média | Alta | Monitorar endpoints com testes automatizados via Postman |
| **R2** | Tempo de resposta acima de 1 segundo | Alta | Média | Otimizar o backend e limitar carga de requisições |
| **R3** | Páginas administrativas acessadas sem login | Baixa | Alta | Implementar verificação de autenticação e tokens |
| **R4** | Dados inválidos aceitos no cadastro | Média | Média | Validar campos obrigatórios no frontend e backend |
| **R5** | API do Google Maps fora do ar ou com erros | Baixa | Alta | Tratar falhas na resposta da API com mensagens amigáveis |
| **R6** | Dificuldade de uso por parte de usuários | Média | Média | Criar interface simples e responsiva; instruções visuais |
| **R7** | Dados não salvos por falha de conexão | Média | Alta | Criar sistema de feedback em tempo real e salvar em cache |
| **R8** | Ataques de injeção ou acessos maliciosos | Baixa | Alta | Implementar filtros, logs e medidas básicas de segurança |

---

## 11. Tabela de Decisão

| Operação | Condição (Dados Válidos) | Condição (Preenchimento Completo) | Resultado Esperado | Exibição Visual |
| :--- | :--- | :--- | :--- | :--- |
| **Pontos de Coleta Próximos** | Sim | Sim | Lista de pontos de coleta (Status 200) | Status code |
| | Não | Não | Erro ao buscar pontos de coleta (Status 400) | Status code |
| **Cadastrar Novo Ponto** | Sim | Sim | Mensagem: Formulário enviado com sucesso! (Status 200) | Script na tela |
| | Não | Não | Dados de preenchimento incorreto (Status 400) | Status code |
| **Administração** | Sim | Sim | Painel administrativo (Status 200) | Painel visível |
| | Não | Não | Mensagem: Email ou senha inválidos (Status 400) | Script na tela |

---

## 12. Matriz de Rastreio

| Seção | ID Requisito | Descrição do Requisito | ID Caso de Teste | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Acesso Público** | RQ01 | Home - Inicial - Apresentação | CT001 | Implementado |
| | RQ02 | Sobre - Informações da organização | CT002 | Implementado |
| | RQ03 | Pontos de Coleta - Listar pontos | CT003 | Implementado |
| | RQ04 | Cadastrar novos pontos coleta - Formulários | CT004 | Implementado |
| | RQ05 | Termos e Condições | CT005 | Implementado |
| | RQ06 | Política de privacidade | CT006 | Implementado |
| | RQ07 | Login - acesso administrativo | CT007 | Implementado |
| **Acesso Restrito** | RQ08 | Painel do Admin | CT008 | Implementado |
| | RQ09 | Cadastro de Ponto | CT009 | Implementado |
| | RQ10 | Cadastrar de Administrador | CT010 | Implementado |
| | RQ11 | Alterar Administrador | CT011 | Implementado |
| | RQ12 | Gerar relatório de pontos cadastrados | CT012 | Implementado |
| | RQ13 | Alterar Ponto de Coleta | CT013 | Implementado |

---

## 13. Responsáveis e Funções

| Responsáveis | Funções |
| :--- | :--- |
| **Clayton Campos de Santana Filho** | Gerência do Projeto |
| **Viviane Santos Gonçalves** | Gerência do Projeto |
| **Agenor Antonio Silva Neto** | Documentação |
| **Eduardo Machado e Silva** | Tester QA |
| **Lenderson Moreira Bispo de Araujo** | Arquitetura e Desenvolvimento |
| **Rogério Rocha Vieira** | Arquitetura e Desenvolvimento |
| **Ingrid Santos de Oliveira** | Design e Interface |

---

## 14. Envolvidos (Stakeholders)

* Univesp.
* Espaço MIDH.
* Doadores

---

## 15. Conclusão / Considerações Finais

O plano de teste desenvolvido para o projeto **Tem Agasalho Aqui** cobre os principais fluxos do sistema, com foco em validar os *endpoints* públicos e administrativos, garantir o bom desempenho das requisições e verificar o comportamento esperado em diferentes situações.

Testes executados e documentados são base sólida para futuras validações, apoiando a equipe de desenvolvimento e promovendo maior qualidade e confiança na aplicação antes de sua publicação oficial. O sistema possui potencial social relevante e, por isso, reforça-se a importância de testes contínuos e automatizados, com atenção especial à segurança e acessibilidade.

---

## 16. Anexos - Postman

| Descrição | Resultados |
| :--- | :--- |
| Link para coleção de testes no Postman via web | [https://documenter.getpostman.com/view/39601139/2sB2j98p3D](https://documenter.getpostman.com/view/39601139/2sB2j98p3D) |
| Automatização (Total de Testes) | 1300 testes executados |
| Runers (Total de Execuções) | 7 execuções |
| QI (Quantidade de Iterações) | 50 |
| Passed (Testes que passaram) | 1292 |
| Failed (Falhas, testes que apresentaram falhas) | 8 |

---

![Coleção de teste](img\postman1.png)

## 17. Registro de Falhas e Bugs

* Registros de falha no tempo de respostas da requisição - tempo de resposta maior que 200 ms.

![Coleção de teste](img\postman2.png)
![Coleção de teste](img\postman3.png)

---

## 18. Melhorias

| Seção | Página | Sugestões / Melhorias |
| :--- | :--- | :--- |
| **Acesso Público** | Pontos de Coleta | Inserir texto explicativo sobre a funcionalidade e retorno do uso mapa gps. |
| | Cadastro | Melhorar validação de campos: Número e Telefone devem aceitar apenas inteiros. Incluir acessibilidade na página. |
| **Administração** | Todas | Incluir acessibilidade na página. |