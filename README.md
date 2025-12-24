# n8n-basic-project

Projeto básico demonstrativo no **n8n**.

Este workflow simples faz o seguinte fluxo:

1. Recebe uma mensagem de chat (via **Chat Trigger**)
2. Extrai o ID da conversa e a mensagem enviada
3. **Salva** imediatamente essas informações em uma planilha do Google Sheets (colunas: `idConversa` e `Mensagem`)
4. Envia a mensagem para um **AI Agent** (usando Groq + Llama 3.3 70B) com memória simples e ferramentas básicas (calculadora + Wikipedia)
5. A resposta da IA **não é salva** na planilha (apenas o input do usuário é registrado)

Objetivo: Mostrar uma integração rápida entre chat → Google Sheets → IA com Groq.

### Tecnologias / Serviços utilizados
- n8n (Chat Trigger + LangChain nodes)
- Google Sheets (para log simples de mensagens)
- Groq API (modelo Llama 3.3 70B)
- Ferramentas: Calculadora e Wikipedia

### Como usar / importar no seu n8n

1. Acesse o seu n8n
2. Vá em **Workflows** → **Import from File** (ou arraste o arquivo JSON diretamente no canvas)
3. Ou use **Import from URL** com o link raw do arquivo neste repositório:
4. **Crie as credenciais manualmente** (elas não vêm no JSON por segurança):
- Google Sheets OAuth2 (precisa de acesso à planilha desejada)
- Groq API Key

5. **Atualize o ID da planilha**:
- No node "Append row in sheet", troque o `documentId` pelo ID da sua própria planilha Google Sheets.
- O workflow foi configurado com um placeholder genérico.

### Estrutura da planilha esperada
Crie uma planilha com pelo menos estas colunas (na ordem):
- idConversa (string)
- Mensagem (string)

O workflow adiciona uma nova linha a cada mensagem recebida.
