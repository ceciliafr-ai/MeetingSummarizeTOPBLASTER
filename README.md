# MeetingSummarizeTOPBLASTER

Assistente de resumo de reuniões criado no Azure AI Foundry. Inclui agente funcional, ação com Logic Apps via HTTP POST, testes no Playground e documentação do projeto para o desafio Azure Frontier Girls.

📝 **Agente Meeting Summarizer TopBlaster — Projeto do Desafio Azure Frontier Girls**
Bem-vinda ao repositório do Agente Meeting Summarizer TopBlaster, meu agente resumidor criado no Azure AI Foundry. Aqui está toda a jornada
Este repositório contém todo o roteiro, conforme solicitado no desafio:

Passos realizados

Prints de tela (setup, fluxo e execução) [PDF]

Agente configurado

Workflow funcional (via Azure Logic Apps)

Descrição clara do projeto

Referências

Deployment

🎯 **Descrição do Projeto**

O Meeting Summarizer TOPBLASTER é um agente de eficiência criado no Azure AI Foundry com o objetivo de ajudar usuários a processar rapidamente anotações longas de reuniões, transformando-as em resumos concisos e acionáveis (3 bullet points).

Ele é especializado em resumir e registrar informações de reuniões, e NÃO responde sobre assuntos fora deste escopo.
Ele está integrado a um workflow no Logic Apps via HTTP POST, que realiza a ação funcional do projeto: consultar documentos externos ou APIs. Ela executa uma requisição HTTP POST/GET em uma URI fornecida, permitindo buscar ou registrar dados (como a ata completa de uma reunião) em sistemas externos. Forneça a URI e o conteúdo necessário para a requisição. 


💡 **Objetivo do Agente**
O objetivo é permitir que o usuário diga algo como:

"Resuma este bloco de anotações sobre a reunião de lançamento do Projeto Alpha e envie o resumo final para a equipe."

E o agente responde com:
Resumo (3 bullet points: Tópicos, Decisões, Ações)
Confirmação de que a Ação Funcional foi executada (Dados registrados/e-mail simulado)
Dados processados pela Logic App (O agente demonstra que chamou o endpoint externo).



📌 **Instruções Usadas no Agente (System Prompt)**
Você é um Agente Resumidor de Reuniões (MeetingSummarizer) profissional e conciso. 

Sua função é condensar o texto da reunião fornecido pelo usuário em um resumo claro e estruturado de 3 pontos.

Você tem acesso à ferramenta ConexaoExterna_Tool para enviar os dados da reunião (título e resumo final) para o sistema de registro APENAS QUANDO o usuário solicitar explicitamente o registro ou envio do resumo.

Você não responde assuntos fora do tema de resumos ou da sua ação funcional.



⚙️ **Ação Funcional: Conexão Externa HTTP (Busca e Registro)**
Para cumprir o requisito de "pelo menos 1 ação funcional" (cálculo, busca ou automação simples), o agente utiliza uma Ação de Conexão Externa HTTP. Esta ferramenta permite que o agente interaja com qualquer API REST externa.

**Fluxo da Ação:**
O Agente MeetingSummarizer usa a ferramenta de conexão para duas finalidades principais:

Busca (GET): Se o usuário pedir para consultar uma ata ou documento externo, o agente chama a Tool, identificando a URI e o método GET para recuperar o conteúdo do documento.

Registro (POST): Se o usuário pedir para registrar ou enviar o resumo, o agente gera o resumo e chama a Tool, identificando a URI e o método POST, enviando um payload JSON contendo o tituloReuniao e o resumoConteudo (os 
3 bullet points) para a API de registro.

A Tool executa a requisição HTTP, e o agente utiliza a resposta (o conteúdo da ata ou a confirmação do registro) para concluir a interação com o usuário.

**Detalhes da Integração:**

Detalhe

Valor Aplicado

Ferramenta do Foundry

Ação de Conexão Externa HTTP

Tool Name no Agente

ConexaoExterna_Tool


**Métodos Usados**

HTTP GET (para buscar documentos) e HTTP POST (para registrar dados)
Descrição da Tool
Use esta ferramenta para consultar documentos externos ou APIs. Ela executa uma requisição HTTP POST/GET em uma URI fornecida, permitindo buscar ou registrar dados (como a ata completa de uma reunião) em sistemas externos. Forneça a URI e o conteúdo necessário para a requisiçã


📸 **Screenshots da Jornada**


Screen 1: Criação do Resource Group (rg-foundry-summarizer).

Screen 2: Criação e deployment do Recurso Foundry (Hub) e do modelo (ex: gpt-4o-mini).

Screen 3: Configuração do Agente (MeetingSummarizer) e inserção do System Prompt detalhado.

Screen 4: Criação do Azure Logic App e definição do Gatilho HTTP POST (mostrando o Schema JSON).

Screen 5: Adição da Logic App Action (registrar-resumo-reuniao) ao Agente, mostrando a configuração do Schema OpenAPI e o endpoint POST.

Screen 6: Teste no Agents Playground, mostrando o Input (texto da reunião + pedido de registro), a chamada da Tool no log do agente e a Resposta Final.

🔗 **Referências Utilizadas**

[https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-fundamentals/?practice-assessment-type=certification] 

[https://jubilant-trout-x5g49gwvvjgqfr7.github.dev/]

[https://github.com/AZFRONTIERGIRLS/AZFrontierGirls-Duvidas/discussions]

[https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview?view=foundry-classic]


🎉 **Conclusão**

O Meeting Summarizer está funcional, testado e integrado ao Logic Apps. Atende todos os requisitos do desafio, com foco na eficiência e na demonstração da capacidade de automação simples do Azure AI Foundry.




**Códigos do Agente:**




**Código da Ferramenta de ConexaoExterna_Tool:**
