---
name: crisp-mcp
description: Skill da REST API do Crisp na MCP.AI: 237 endpoints em /api/crisp. Atendimento ao cliente, chat ao vivo, CRM e helpdesk no Crisp com a REST API oficial v1 completa (api.crisp.chat), conversas e mensagens, contatos/pessoas, base de conhecimento (artigos, categorias, idiomas), campanhas, operadores, visitantes e configurações do site. Consulta e operação. Autenticação por par de tokens (gerado no Crisp, em Settings, Workspace settings, Advanced configuration). Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Crisp — REST API skill

Você tem acesso à **Crisp** REST API na MCP.AI.

> Atendimento ao cliente, chat ao vivo, CRM e helpdesk no Crisp com a REST API oficial v1 completa (api.crisp.chat), conversas e mensagens, contatos/pessoas, base de conhecimento (artigos, categorias, idiomas), campanhas, operadores, visitantes e configurações do site. Consulta e operação. Autenticação por par de tokens (gerado no Crisp, em Settings, Workspace settings, Advanced configuration).

## Base URL

```
https://api.mcp.ai/api/crisp
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/crisp/abort/ongoing/call/session/for/conversation \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"sessionID":"...","callID":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/crisp/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (237)

#### `crisp_abort_ongoing_call_session_for_conversation`

Abort Ongoing Call Session For Conversation (DELETE /website/{websiteID}/conversation/{sessionID}/call/{callID}). _(POST /api/crisp/abort/ongoing/call/session/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `callID` | string | Sim | Path param "callID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_abort_website_deletion`

Abort Website Deletion (DELETE /website/{websiteID}/expunge). _(POST /api/crisp/abort/website/deletion)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_helpdesk_locale`

Add Helpdesk Locale (POST /website/{websiteID}/helpdesk/locale). _(POST /api/crisp/add/helpdesk/locale)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_helpdesk_locale_category`

Add Helpdesk Locale Category (POST /website/{websiteID}/helpdesk/locale/{locale}/category). _(POST /api/crisp/add/helpdesk/locale/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_helpdesk_locale_section`

Add Helpdesk Locale Section (POST /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/section). _(POST /api/crisp/add/helpdesk/locale/section)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_helpdesk_redirection`

Add Helpdesk Redirection (POST /website/{websiteID}/helpdesk/redirection). _(POST /api/crisp/add/helpdesk/redirection)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_new_helpdesk_locale_article`

Add A New Helpdesk Locale Article (POST /website/{websiteID}/helpdesk/locale/{locale}/article). _(POST /api/crisp/add/new/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_new_people_profile`

Add New People Profile (POST /website/{websiteID}/people/profile). _(POST /api/crisp/add/new/people/profile)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_add_people_event`

Add A People Event (POST /website/{websiteID}/people/events/{peopleID}). _(POST /api/crisp/add/people/event)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_assign_conversation_routing`

Assign Conversation Routing (PATCH /website/{websiteID}/conversation/{sessionID}/routing). _(POST /api/crisp/assign/conversation/routing)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_assist_existing_browsing_session`

Assist Existing Browsing Session (PATCH /website/{websiteID}/conversation/{sessionID}/browsing/{browsingID}/assist). _(POST /api/crisp/assist/existing/browsing/session)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `browsingID` | string | Sim | Path param "browsingID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_block_conversations`

Batch Block Conversations (PATCH /website/{websiteID}/batch/block). _(POST /api/crisp/batch/block/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_inbox_conversations`

Batch Inbox Conversations (PATCH /website/{websiteID}/batch/inbox). _(POST /api/crisp/batch/inbox/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_order_inboxes`

Batch Order Inboxes (PATCH /website/{websiteID}/inboxes/batch/order). _(POST /api/crisp/batch/order/inboxes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_read_conversations`

Batch Read Conversations (PATCH /website/{websiteID}/batch/read). _(POST /api/crisp/batch/read/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_remove_conversations`

Batch Remove Conversations (PATCH /website/{websiteID}/batch/remove). _(POST /api/crisp/batch/remove/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_remove_people`

Batch Remove People (PATCH /website/{websiteID}/batch/remove). _(POST /api/crisp/batch/remove/people)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_report_conversations`

Batch Report Conversations (POST /website/{websiteID}/batch/report). _(POST /api/crisp/batch/report/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_resolve_conversations`

Batch Resolve Conversations (PATCH /website/{websiteID}/batch/resolve). _(POST /api/crisp/batch/resolve/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_routing_conversations`

Batch Routing Conversations (PATCH /website/{websiteID}/batch/routing). _(POST /api/crisp/batch/routing/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_unread_conversations`

Batch Unread Conversations (PATCH /website/{websiteID}/batch/unread). _(POST /api/crisp/batch/unread/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_unresolve_conversations`

Batch Unresolve Conversations (PATCH /website/{websiteID}/batch/unresolve). _(POST /api/crisp/batch/unresolve/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_update_conversations_data`

Batch Update Conversations Data (PATCH /website/{websiteID}/batch/data). _(POST /api/crisp/batch/update/conversations/data)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_update_conversations_segments`

Batch Update Conversations Segments (PATCH /website/{websiteID}/batch/segments). _(POST /api/crisp/batch/update/conversations/segments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_update_people_data`

Batch Update People Data (PATCH /website/{websiteID}/batch/data). _(POST /api/crisp/batch/update/people/data)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_batch_update_people_segments`

Batch Update People Segments (PATCH /website/{websiteID}/batch/segments). _(POST /api/crisp/batch/update/people/segments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_block_incoming_messages_for_conversation`

Block Incoming Messages For Conversation (PATCH /website/{websiteID}/conversation/{sessionID}/block). _(POST /api/crisp/block/incoming/messages/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_change_bill_period_for_website_plan_subscription`

Change Bill Period For Website Plan Subscription (PATCH /plans/subscription/{websiteID}/bill/period). _(POST /api/crisp/change/bill/period/for/website/plan/subscription)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_change_conversation_state`

Change Conversation State (PATCH /website/{websiteID}/conversation/{sessionID}/state). _(POST /api/crisp/change/conversation/state)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_change_operator_membership`

Change Operator Membership (PATCH /website/{websiteID}/operator/{userID}). _(POST /api/crisp/change/operator/membership)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `userID` | string | Sim | Path param "userID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_check_campaign_exists`

Check If Campaign Exists (HEAD /website/{websiteID}/campaign/{campaignID}). _(POST /api/crisp/check/campaign/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_campaign_template_exists`

Check If Campaign Template Exists (HEAD /website/{websiteID}/campaigns/template/{templateID}). _(POST /api/crisp/check/campaign/template/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `templateID` | string | Sim | Path param "templateID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_connect_session_validity`

Check Connect Session Validity (HEAD /plugin/connect/session). _(POST /api/crisp/check/connect/session/validity)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_conversation_exists`

Check If Conversation Exists (HEAD /website/{websiteID}/conversation/{sessionID}). _(POST /api/crisp/check/conversation/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_coupon_availability_for_website_plan_subscription`

Check Coupon Availability For Website Plan Subscription (GET /plans/subscription/{websiteID}/coupon). _(POST /api/crisp/check/coupon/availability/for/website/plan/subscription)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_exists`

Check If Helpdesk Exists (HEAD /website/{websiteID}/helpdesk). _(POST /api/crisp/check/helpdesk/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_locale_article_alternate_exists`

Check If Helpdesk Locale Article Alternate Exists (HEAD /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/alternate/{localeLinked}). _(POST /api/crisp/check/helpdesk/locale/article/alternate/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `localeLinked` | string | Sim | Path param "localeLinked" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_locale_article_exists`

Check If Helpdesk Locale Article Exists (HEAD /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}). _(POST /api/crisp/check/helpdesk/locale/article/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_locale_category_exists`

Check If Helpdesk Locale Category Exists (HEAD /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}). _(POST /api/crisp/check/helpdesk/locale/category/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_locale_exists`

Check If Helpdesk Locale Exists (HEAD /website/{websiteID}/helpdesk/locale/{locale}). _(POST /api/crisp/check/helpdesk/locale/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_locale_section_exists`

Check If Helpdesk Locale Section Exists (HEAD /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/section/{sectionId}). _(POST /api/crisp/check/helpdesk/locale/section/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `sectionId` | string | Sim | Path param "sectionId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_helpdesk_redirection_exists`

Check If Helpdesk Redirection Exists (HEAD /website/{websiteID}/helpdesk/redirection/{redirectionId}). _(POST /api/crisp/check/helpdesk/redirection/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `redirectionId` | string | Sim | Path param "redirectionId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_inbox_exists`

Check If Inbox Exists (HEAD /website/{websiteID}/inbox/{inboxID}). _(POST /api/crisp/check/inbox/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `inboxID` | string | Sim | Path param "inboxID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_people_profile_exists`

Check If People Profile Exists (HEAD /website/{websiteID}/people/profile/{peopleID}). _(POST /api/crisp/check/people/profile/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_check_website_exists`

Check If Website Exists (HEAD /website). _(POST /api/crisp/check/website/exists)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_clear_blocked_visitors_in_rule`

Clear Blocked Visitors In Rule (DELETE /website/{websiteID}/visitors/blocked/{rule}). _(POST /api/crisp/clear/blocked/visitors/in/rule)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `rule` | string | Sim | Path param "rule" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_compose_message_in_conversation`

Compose A Message In Conversation (PATCH /website/{websiteID}/conversation/{sessionID}/compose). _(POST /api/crisp/compose/message/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_count_blocked_visitors`

Count Blocked Visitors (GET /website/{websiteID}/visitors/blocked). _(POST /api/crisp/count/blocked/visitors)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_count_blocked_visitors_in_rule`

Count Blocked Visitors In Rule (GET /website/{websiteID}/visitors/blocked/{rule}). _(POST /api/crisp/count/blocked/visitors/in/rule)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `rule` | string | Sim | Path param "rule" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_count_visitors`

Count Visitors (GET /website/{websiteID}/visitors/count). _(POST /api/crisp/count/visitors)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_create_new_campaign`

Create A New Campaign (POST /website/{websiteID}/campaign). _(POST /api/crisp/create/new/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_create_new_campaign_template`

Create A New Campaign Template (POST /website/{websiteID}/campaigns/template). _(POST /api/crisp/create/new/campaign/template)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_create_new_conversation`

Create A New Conversation (POST /website/{websiteID}/conversation). _(POST /api/crisp/create/new/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_create_new_inbox`

Create A New Inbox (POST /website/{websiteID}/inbox). _(POST /api/crisp/create/new/inbox)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_create_website`

Create Website (POST /website). _(POST /api/crisp/create/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk`

Delete Helpdesk (DELETE /website/{websiteID}/helpdesk). _(POST /api/crisp/delete/helpdesk)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk_locale`

Delete Helpdesk Locale (DELETE /website/{websiteID}/helpdesk/locale/{locale}). _(POST /api/crisp/delete/helpdesk/locale)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk_locale_article`

Delete Helpdesk Locale Article (DELETE /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}). _(POST /api/crisp/delete/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk_locale_article_alternate`

Delete Helpdesk Locale Article Alternate (DELETE /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/alternate/{localeLinked}). _(POST /api/crisp/delete/helpdesk/locale/article/alternate)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `localeLinked` | string | Sim | Path param "localeLinked" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk_locale_category`

Delete Helpdesk Locale Category (DELETE /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}). _(POST /api/crisp/delete/helpdesk/locale/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk_locale_section`

Delete Helpdesk Locale Section (DELETE /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/section/{sectionId}). _(POST /api/crisp/delete/helpdesk/locale/section)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `sectionId` | string | Sim | Path param "sectionId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_helpdesk_redirection`

Delete Helpdesk Redirection (DELETE /website/{websiteID}/helpdesk/redirection/{redirectionId}). _(POST /api/crisp/delete/helpdesk/redirection)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `redirectionId` | string | Sim | Path param "redirectionId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_inbox`

Delete Inbox (DELETE /website/{websiteID}/inbox/{inboxID}). _(POST /api/crisp/delete/inbox)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `inboxID` | string | Sim | Path param "inboxID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_suggested_conversation_data_key`

Delete Suggested Conversation Data Key (DELETE /website/{websiteID}/conversations/suggest/data). _(POST /api/crisp/delete/suggested/conversation/data/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_suggested_conversation_segment`

Delete Suggested Conversation Segment (DELETE /website/{websiteID}/conversations/suggest/segment). _(POST /api/crisp/delete/suggested/conversation/segment)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_suggested_people_data_key`

Delete Suggested People Data Key (DELETE /website/{websiteID}/people/suggest/data). _(POST /api/crisp/delete/suggested/people/data/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_suggested_people_event`

Delete Suggested People Event (DELETE /website/{websiteID}/people/suggest/event). _(POST /api/crisp/delete/suggested/people/event)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_suggested_people_segment`

Delete Suggested People Segment (DELETE /website/{websiteID}/people/suggest/segment). _(POST /api/crisp/delete/suggested/people/segment)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_delete_website`

Delete A Website (DELETE /website/{websiteID}). _(POST /api/crisp/delete/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_deliver_widget_button_action_for_conversation`

Deliver Widget Button Action For Conversation (POST /website/{websiteID}/conversation/{sessionID}/widget/{pluginID}/button). _(POST /api/crisp/deliver/widget/button/action/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_deliver_widget_data_edit_action_for_conversation`

Deliver Widget Data Edit Action For Conversation (POST /website/{websiteID}/conversation/{sessionID}/widget/{pluginID}/data). _(POST /api/crisp/deliver/widget/data/edit/action/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_deliver_widget_data_fetch_action_for_conversation`

Deliver Widget Data Fetch Action For Conversation (POST /website/{websiteID}/conversation/{sessionID}/widget/{pluginID}/data). _(POST /api/crisp/deliver/widget/data/fetch/action/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_dispatch_campaign`

Dispatch A Campaign (POST /website/{websiteID}/campaign/{campaignID}/dispatch). _(POST /api/crisp/dispatch/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_dispatch_plugin_event`

Dispatch Plugin Event (POST /plugins/subscription/{websiteID}/{pluginID}/event). _(POST /api/crisp/dispatch/plugin/event)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_export_helpdesk_locale_articles`

Export Helpdesk Locale Articles (POST /website/{websiteID}/helpdesk/locale/{locale}/export). _(POST /api/crisp/export/helpdesk/locale/articles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_export_people_profiles`

Export People Profiles (POST /website/{websiteID}/people/export/profiles). _(POST /api/crisp/export/people/profiles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_flush_last_active_website_operators`

Flush Last Active Website Operators (DELETE /website/{websiteID}/operators/active). _(POST /api/crisp/flush/last/active/website/operators)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_forward_plugin_payload_to_channel`

Forward Plugin Payload To Channel (POST /plugins/subscription/{websiteID}/{pluginID}/channel). _(POST /api/crisp/forward/plugin/payload/to/channel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_generate_analytics`

Generate Analytics (POST /website/{websiteID}/analytics/generate). _(POST /api/crisp/generate/analytics)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_generate_helpdesk_domain_setup_flow`

Generate Helpdesk Domain Setup Flow (GET /website/{websiteID}/helpdesk/domain/setup). _(POST /api/crisp/generate/helpdesk/domain/setup/flow)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_block_status_for_conversation`

Get Block Status For Conversation (GET /website/{websiteID}/conversation/{sessionID}/block). _(POST /api/crisp/get/block/status/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_campaign`

Get A Campaign (GET /website/{websiteID}/campaign/{campaignID}). _(POST /api/crisp/get/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_campaign_template`

Get A Campaign Template (GET /website/{websiteID}/campaigns/template/{templateID}). _(POST /api/crisp/get/campaign/template)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `templateID` | string | Sim | Path param "templateID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_connect_account`

Get Connect Account (GET /plugin/connect/account). _(POST /api/crisp/get/connect/account)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_conversation`

Get A Conversation (GET /website/{websiteID}/conversation/{sessionID}). _(POST /api/crisp/get/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_conversation_metas`

Get Conversation Metas (GET /website/{websiteID}/conversation/{sessionID}/meta). _(POST /api/crisp/get/conversation/metas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_conversation_participants`

Get Conversation Participants (GET /website/{websiteID}/conversation/{sessionID}/participants). _(POST /api/crisp/get/conversation/participants)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_conversation_relations`

Get Conversation Relations (GET /website/{websiteID}/conversation/{sessionID}/relations). _(POST /api/crisp/get/conversation/relations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_conversation_routing_assign`

Get Conversation Routing Assign (GET /website/{websiteID}/conversation/{sessionID}/routing). _(POST /api/crisp/get/conversation/routing/assign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_conversation_state`

Get Conversation State (GET /website/{websiteID}/conversation/{sessionID}/state). _(POST /api/crisp/get/conversation/state)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_inbox`

Get Inbox (GET /website/{websiteID}/inbox/{inboxID}). _(POST /api/crisp/get/inbox)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `inboxID` | string | Sim | Path param "inboxID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_message_in_conversation`

Get A Message In Conversation (GET /website/{websiteID}/conversation/{sessionID}/message/{fingerprint}). _(POST /api/crisp/get/message/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `fingerprint` | string | Sim | Path param "fingerprint" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_messages_in_conversation`

Get Messages In Conversation (GET /website/{websiteID}/conversation/{sessionID}/messages). _(POST /api/crisp/get/messages/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_ongoing_call_session_for_conversation`

Get Ongoing Call Session For Conversation (GET /website/{websiteID}/conversation/{sessionID}/call). _(POST /api/crisp/get/ongoing/call/session/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_original_message_in_conversation`

Get An Original Message In Conversation (GET /website/{websiteID}/conversation/{sessionID}/original/{originalID}). _(POST /api/crisp/get/original/message/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `originalID` | string | Sim | Path param "originalID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_people_data`

Get People Data (GET /website/{websiteID}/people/data/{peopleID}). _(POST /api/crisp/get/people/data)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_people_profile`

Save People Profile (GET /website/{websiteID}/people/profile/{peopleID}). _(POST /api/crisp/get/people/profile)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_people_statistics`

Get People Statistics (GET /website/{websiteID}/people/stats). _(POST /api/crisp/get/people/statistics)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_people_subscription_status`

Get People Subscription Status (GET /website/{websiteID}/people/subscription/{peopleID}). _(POST /api/crisp/get/people/subscription/status)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_plan_subscription_for_website`

Get Plan Subscription For A Website (GET /plans/subscription/{websiteID}). _(POST /api/crisp/get/plan/subscription/for/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_plugin_attest_provenance`

Get Plugin Attest Provenance (GET /plugins/subscription/{websiteID}/{pluginID}/attest/provenance). _(POST /api/crisp/get/plugin/attest/provenance)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_plugin_usage_bills`

Get Plugin Usage Bills (GET /plugins/subscription/{websiteID}/{pluginID}/bill/usage). _(POST /api/crisp/get/plugin/usage/bills)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_session_identifier_from_token`

Get Session Identifier From Token (GET /website/{websiteID}/visitors/token/{tokenID}). _(POST /api/crisp/get/session/identifier/from/token)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `tokenID` | string | Sim | Path param "tokenID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_subscription_details`

Get Subscription Details (GET /plugins/subscription/{websiteID}/{pluginID}). _(POST /api/crisp/get/subscription/details)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_subscription_settings`

Get Subscription Settings (GET /plugins/subscription/{websiteID}/{pluginID}/settings). _(POST /api/crisp/get/subscription/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_verify_key`

Get Verify Key (GET /website/{websiteID}/verify/key). _(POST /api/crisp/get/verify/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_verify_settings`

Get Verify Settings (GET /website/{websiteID}/verify/settings). _(POST /api/crisp/get/verify/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_verify_status_for_conversation`

Get Verify Status For Conversation (GET /website/{websiteID}/conversation/{sessionID}/verify). _(POST /api/crisp/get/verify/status/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_website`

Get A Website (GET /website/{websiteID}). _(POST /api/crisp/get/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_website_availability_status`

Get Website Availability Status (GET /website/{websiteID}/availability/status). _(POST /api/crisp/get/website/availability/status)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_website_operator`

Get A Website Operator (GET /website/{websiteID}/operator/{userID}). _(POST /api/crisp/get/website/operator)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `userID` | string | Sim | Path param "userID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_get_website_settings`

Get Website Settings (GET /website/{websiteID}/settings). _(POST /api/crisp/get/website/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_import_external_helpdesk_to_locale`

Import External Helpdesk To Locale (POST /website/{websiteID}/helpdesk/locale/{locale}/import). _(POST /api/crisp/import/external/helpdesk/to/locale)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_import_people_profiles`

Import People Profiles (POST /website/{websiteID}/people/import/profiles). _(POST /api/crisp/import/people/profiles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_initialize_helpdesk`

Initialize Helpdesk (POST /website/{websiteID}/helpdesk). _(POST /api/crisp/initialize/helpdesk)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_initiate_browsing_session_for_conversation`

Initiate Browsing Session For Conversation (POST /website/{websiteID}/conversation/{sessionID}/browsing). _(POST /api/crisp/initiate/browsing/session/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_initiate_conversation_with_existing_session`

Initiate A Conversation With Existing Session (POST /website/{websiteID}/conversation/{sessionID}/initiate). _(POST /api/crisp/initiate/conversation/with/existing/session)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_initiate_new_call_session_for_conversation`

Initiate New Call Session For Conversation (POST /website/{websiteID}/conversation/{sessionID}/call). _(POST /api/crisp/initiate/new/call/session/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_invite_website_operator`

Invite A Website Operator (POST /website/{websiteID}/operator). _(POST /api/crisp/invite/website/operator)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_list_accounts`

Lista as conexões (contas) Crisp vinculadas a este install — id, label, website. _(POST /api/crisp/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |

#### `crisp_list_all_connect_websites`

List All Connect Websites (GET /plugin/connect/websites/all/{pageNumber}). _(POST /api/crisp/list/all/connect/websites)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_browsing_sessions_for_conversation`

List Browsing Sessions For Conversation (GET /website/{websiteID}/conversation/{sessionID}/browsing). _(POST /api/crisp/list/browsing/sessions/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_campaign_recipients`

List Campaign Recipients (GET /website/{websiteID}/campaign/{campaignID}/recipients/{pageNumber}). _(POST /api/crisp/list/campaign/recipients)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_campaign_statistics`

List Campaign Statistics (GET /website/{websiteID}/campaign/{campaignID}/statistics/{action}/{pageNumber}). _(POST /api/crisp/list/campaign/statistics)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `action` | string | Sim | Path param "action" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_campaign_tags`

List Campaign Tags (GET /website/{websiteID}/campaigns/tags). _(POST /api/crisp/list/campaign/tags)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_campaign_templates`

List Campaign Templates (GET /website/{websiteID}/campaigns/templates/{pageNumber}). _(POST /api/crisp/list/campaign/templates)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_campaigns`

List Campaigns (GET /website/{websiteID}/campaigns/list/{pageNumber}). _(POST /api/crisp/list/campaigns)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_connect_websites_since`

List Connect Websites Since (GET /plugin/connect/websites/since). _(POST /api/crisp/list/connect/websites/since)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_conversation_events`

List Conversation Events (GET /website/{websiteID}/conversation/{sessionID}/events/{pageNumber}). _(POST /api/crisp/list/conversation/events)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_conversation_files`

List Conversation Files (GET /website/{websiteID}/conversation/{sessionID}/files/{pageNumber}). _(POST /api/crisp/list/conversation/files)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_conversation_pages`

List Conversation Pages (GET /website/{websiteID}/conversation/{sessionID}/pages/{pageNumber}). _(POST /api/crisp/list/conversation/pages)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_conversations`

List Conversations (GET /website/{websiteID}/conversations/{pageNumber}). _(POST /api/crisp/list/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_locale_article_alternates`

List Helpdesk Locale Article Alternates (GET /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/alternates). _(POST /api/crisp/list/helpdesk/locale/article/alternates)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_locale_articles`

List Helpdesk Locale Articles (GET /website/{websiteID}/helpdesk/locale/{locale}/articles/{pageNumber}). _(POST /api/crisp/list/helpdesk/locale/articles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_locale_categories`

List Helpdesk Locale Categories (GET /website/{websiteID}/helpdesk/locale/{locale}/categories/{pageNumber}). _(POST /api/crisp/list/helpdesk/locale/categories)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_locale_feedbacks`

List Helpdesk Locale Feedbacks (GET /website/{websiteID}/helpdesk/locale/{locale}/feedback/list/{pageNumber}). _(POST /api/crisp/list/helpdesk/locale/feedbacks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_locale_sections`

List Helpdesk Locale Sections (GET /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/sections/{pageNumber}). _(POST /api/crisp/list/helpdesk/locale/sections)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_locales`

List Helpdesk Locales (GET /website/{websiteID}/helpdesk/locales/{pageNumber}). _(POST /api/crisp/list/helpdesk/locales)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_helpdesk_redirections`

List Helpdesk Redirections (GET /website/{websiteID}/helpdesk/redirections/{pageNumber}). _(POST /api/crisp/list/helpdesk/redirections)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_inboxes`

List Inboxes (GET /website/{websiteID}/inboxes/list/{pageNumber}). _(POST /api/crisp/list/inboxes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_last_active_website_operators`

List Last Active Website Operators (GET /website/{websiteID}/operators/active). _(POST /api/crisp/list/last/active/website/operators)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_people_campaigns`

List People Campaigns (GET /website/{websiteID}/people/campaigns/{peopleID}/list/{pageNumber}). _(POST /api/crisp/list/people/campaigns)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_people_conversations`

List People Conversations (GET /website/{websiteID}/people/conversations/{peopleID}/list/{pageNumber}). _(POST /api/crisp/list/people/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_people_events`

List People Events (GET /website/{websiteID}/people/events/{peopleID}/list/{pageNumber}). _(POST /api/crisp/list/people/events)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_people_profiles`

List People Profiles (GET /website/{websiteID}/people/profiles/{pageNumber}). _(POST /api/crisp/list/people/profiles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_spam_conversations`

List Spam Conversations (GET /website/{websiteID}/conversations/spams/{pageNumber}). _(POST /api/crisp/list/spam/conversations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_subscriptions_for_website`

List Subscriptions For A Website (GET /plugins/subscription/{websiteID}). _(POST /api/crisp/list/subscriptions/for/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_suggested_conversation_data_keys`

List Suggested Conversation Data Keys (GET /website/{websiteID}/conversations/suggest/data/{pageNumber}). _(POST /api/crisp/list/suggested/conversation/data/keys)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_suggested_conversation_segments`

List Suggested Conversation Segments (GET /website/{websiteID}/conversations/suggest/segments/{pageNumber}). _(POST /api/crisp/list/suggested/conversation/segments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_suggested_people_data_keys`

List Suggested People Data Keys (GET /website/{websiteID}/people/suggest/data/{pageNumber}). _(POST /api/crisp/list/suggested/people/data/keys)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_suggested_people_events`

List Suggested People Events (GET /website/{websiteID}/people/suggest/events/{pageNumber}). _(POST /api/crisp/list/suggested/people/events)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_suggested_people_segments`

List Suggested People Segments (GET /website/{websiteID}/people/suggest/segments/{pageNumber}). _(POST /api/crisp/list/suggested/people/segments)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_visitors`

List Visitors (GET /website/{websiteID}/visitors/list/{pageNumber}). _(POST /api/crisp/list/visitors)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pageNumber` | string | Não | Número da página (paginação). Default "1". |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_website_operator_availabilities`

List Website Operator Availabilities (GET /website/{websiteID}/availability/operators). _(POST /api/crisp/list/website/operator/availabilities)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_list_website_operators`

List Website Operators (GET /website/{websiteID}/operators/list). _(POST /api/crisp/list/website/operators)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_map_helpdesk_locale_feedback_ratings`

Map Helpdesk Locale Feedback Ratings (GET /website/{websiteID}/helpdesk/locale/{locale}/feedback/ratings). _(POST /api/crisp/map/helpdesk/locale/feedback/ratings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_mark_conversation_as_unread`

Mark Conversation As Unread (PATCH /website/{websiteID}/conversation/{sessionID}/unread). _(POST /api/crisp/mark/conversation/as/unread)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_mark_messages_delivered_in_conversation`

Mark Messages As Delivered In Conversation (PATCH /website/{websiteID}/conversation/{sessionID}/delivered). _(POST /api/crisp/mark/messages/delivered/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_mark_messages_read_in_conversation`

Mark Messages As Read In Conversation (PATCH /website/{websiteID}/conversation/{sessionID}/read). _(POST /api/crisp/mark/messages/read/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_pause_campaign`

Pause A Campaign (POST /website/{websiteID}/campaign/{campaignID}/pause). _(POST /api/crisp/pause/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_pinpoint_visitors_on_map`

Pinpoint Visitors On A Map (GET /website/{websiteID}/visitors/map). _(POST /api/crisp/pinpoint/visitors/on/map)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_plans_list_all_active_subscriptions`

List All Active Plan Subscriptions (GET /plans/subscription). _(POST /api/crisp/plans/list/all/active/subscriptions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_plugin_get_connect_endpoints`

Get Connect Endpoints (GET /plugin/connect/endpoints). _(POST /api/crisp/plugin/get/connect/endpoints)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_plugins_list_all_active_subscriptions`

List All Active Subscriptions (GET /plugins/subscription). _(POST /api/crisp/plugins/list/all/active/subscriptions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_publish_helpdesk_locale_article`

Publish Helpdesk Locale Article (POST /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/publish). _(POST /api/crisp/publish/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_redeem_coupon_for_website_plan_subscription`

Redeem Coupon For Website Plan Subscription (PATCH /plans/subscription/{websiteID}/coupon). _(POST /api/crisp/redeem/coupon/for/website/plan/subscription)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_redeem_identity_verification_link_for_conversation`

Redeem Identity Verification Link For Conversation (PUT /website/{websiteID}/conversation/{sessionID}/verify/identity/link). _(POST /api/crisp/redeem/identity/verification/link/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_remove_campaign`

Remove A Campaign (DELETE /website/{websiteID}/campaign/{campaignID}). _(POST /api/crisp/remove/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_remove_campaign_template`

Remove A Campaign Template (DELETE /website/{websiteID}/campaigns/template/{templateID}). _(POST /api/crisp/remove/campaign/template)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `templateID` | string | Sim | Path param "templateID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_remove_conversation`

Remove A Conversation (DELETE /website/{websiteID}/conversation/{sessionID}). _(POST /api/crisp/remove/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_remove_message_in_conversation`

Remove A Message In Conversation (DELETE /website/{websiteID}/conversation/{sessionID}/message/{fingerprint}). _(POST /api/crisp/remove/message/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `fingerprint` | string | Sim | Path param "fingerprint" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_remove_people_profile`

Remove People Profile (DELETE /website/{websiteID}/people/profile/{peopleID}). _(POST /api/crisp/remove/people/profile)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_report_conversation`

Report Conversation (POST /website/{websiteID}/conversation/{sessionID}/report). _(POST /api/crisp/report/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_report_plugin_usage_to_bill`

Report Plugin Usage To Bill (POST /plugins/subscription/{websiteID}/{pluginID}/bill/usage). _(POST /api/crisp/report/plugin/usage/to/bill)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_request_chatbox_binding_purge_for_conversation`

Request Chatbox Binding Purge For Conversation (POST /website/{websiteID}/conversation/{sessionID}/purge). _(POST /api/crisp/request/chatbox/binding/purge/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_request_email_transcript_for_conversation`

Request Email Transcript For Conversation (POST /website/{websiteID}/conversation/{sessionID}/transcript). _(POST /api/crisp/request/email/transcript/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_request_helpdesk_domain_change`

Request Helpdesk Domain Change (PATCH /website/{websiteID}/helpdesk/domain). _(POST /api/crisp/request/helpdesk/domain/change)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_request_identity_verification_for_conversation`

Request Identity Verification For Conversation (POST /website/{websiteID}/conversation/{sessionID}/verify/identity). _(POST /api/crisp/request/identity/verification/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_request_tool_call_for_conversation`

Request Tool Call For Conversation (POST /website/{websiteID}/conversation/{sessionID}/tool). _(POST /api/crisp/request/tool/call/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_request_user_feedback_for_conversation`

Request User Feedback For Conversation (POST /website/{websiteID}/conversation/{sessionID}/feedback). _(POST /api/crisp/request/user/feedback/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk`

Resolve Helpdesk (GET /website/{websiteID}/helpdesk). _(POST /api/crisp/resolve/helpdesk)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_domain`

Resolve Helpdesk Domain (GET /website/{websiteID}/helpdesk/domain). _(POST /api/crisp/resolve/helpdesk/domain)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale`

Resolve Helpdesk Locale (GET /website/{websiteID}/helpdesk/locale/{locale}). _(POST /api/crisp/resolve/helpdesk/locale)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale_article`

Resolve Helpdesk Locale Article (GET /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}). _(POST /api/crisp/resolve/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale_article_alternate`

Resolve Helpdesk Locale Article Alternate (GET /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/alternate/{localeLinked}). _(POST /api/crisp/resolve/helpdesk/locale/article/alternate)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `localeLinked` | string | Sim | Path param "localeLinked" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale_article_category`

Resolve Helpdesk Locale Article Category (GET /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/category). _(POST /api/crisp/resolve/helpdesk/locale/article/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale_article_page`

Resolve Helpdesk Locale Article Page (GET /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/page). _(POST /api/crisp/resolve/helpdesk/locale/article/page)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale_category`

Resolve Helpdesk Locale Category (GET /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}). _(POST /api/crisp/resolve/helpdesk/locale/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_locale_section`

Resolve Helpdesk Locale Section (GET /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/section/{sectionId}). _(POST /api/crisp/resolve/helpdesk/locale/section)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `sectionId` | string | Sim | Path param "sectionId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_redirection`

Resolve Helpdesk Redirection (GET /website/{websiteID}/helpdesk/redirection/{redirectionId}). _(POST /api/crisp/resolve/helpdesk/redirection)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `redirectionId` | string | Sim | Path param "redirectionId" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_helpdesk_settings`

Resolve Helpdesk Settings (GET /website/{websiteID}/helpdesk/settings). _(POST /api/crisp/resolve/helpdesk/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resolve_spam_conversation_content`

Resolve Spam Conversation Content (GET /website/{websiteID}/conversations/spam/{spamID}/content). _(POST /api/crisp/resolve/spam/conversation/content)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `spamID` | string | Sim | Path param "spamID" (obrigatório) |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

#### `crisp_resume_campaign`

Resume A Campaign (POST /website/{websiteID}/campaign/{campaignID}/resume). _(POST /api/crisp/resume/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_roll_verify_key`

Roll Verify Key (POST /website/{websiteID}/verify/key). _(POST /api/crisp/roll/verify/key)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_campaign`

Save A Campaign (PUT /website/{websiteID}/campaign/{campaignID}). _(POST /api/crisp/save/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_campaign_template`

Save A Campaign Template (PUT /website/{websiteID}/campaigns/template/{templateID}). _(POST /api/crisp/save/campaign/template)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `templateID` | string | Sim | Path param "templateID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_conversation_participants`

Save Conversation Participants (PUT /website/{websiteID}/conversation/{sessionID}/participants). _(POST /api/crisp/save/conversation/participants)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_helpdesk_locale_article`

Save Helpdesk Locale Article (PUT /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}). _(POST /api/crisp/save/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_helpdesk_locale_article_alternate`

Save Helpdesk Locale Article Alternate (PUT /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/alternate/{localeLinked}). _(POST /api/crisp/save/helpdesk/locale/article/alternate)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `localeLinked` | string | Sim | Path param "localeLinked" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_helpdesk_locale_category`

Save Helpdesk Locale Category (PUT /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}). _(POST /api/crisp/save/helpdesk/locale/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_helpdesk_locale_section`

Save Helpdesk Locale Section (PUT /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/section/{sectionId}). _(POST /api/crisp/save/helpdesk/locale/section)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `sectionId` | string | Sim | Path param "sectionId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_helpdesk_settings`

Save Helpdesk Settings (PATCH /website/{websiteID}/helpdesk/settings). _(POST /api/crisp/save/helpdesk/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_inbox`

Save Inbox (PUT /website/{websiteID}/inbox/{inboxID}). _(POST /api/crisp/save/inbox)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `inboxID` | string | Sim | Path param "inboxID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_people_data`

Save People Data (PUT /website/{websiteID}/people/data/{peopleID}). _(POST /api/crisp/save/people/data)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_people_profile`

Get People Profile (PUT /website/{websiteID}/people/profile/{peopleID}). _(POST /api/crisp/save/people/profile)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_save_subscription_settings`

Save Subscription Settings (PUT /plugins/subscription/{websiteID}/{pluginID}/settings). _(POST /api/crisp/save/subscription/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_schedule_reminder_for_conversation`

Schedule A Reminder For Conversation (POST /website/{websiteID}/conversation/{sessionID}/reminder). _(POST /api/crisp/schedule/reminder/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_send_action_to_existing_browsing_session`

Send Action To An Existing Browsing Session (PATCH /website/{websiteID}/conversation/{sessionID}/browsing/{browsingID}). _(POST /api/crisp/send/action/to/existing/browsing/session)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `browsingID` | string | Sim | Path param "browsingID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_send_email_to_website_operators`

Send Email To Website Operators (POST /website/{websiteID}/operators/email). _(POST /api/crisp/send/email/to/website/operators)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_send_message_in_conversation`

Send A Message In Conversation (POST /website/{websiteID}/conversation/{sessionID}/message). _(POST /api/crisp/send/message/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_submit_spam_conversation_decision`

Submit Spam Conversation Decision (POST /website/{websiteID}/conversations/spam/{spamID}/decision). _(POST /api/crisp/submit/spam/conversation/decision)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `spamID` | string | Sim | Path param "spamID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_subscribe_website_to_plan`

Subscribe Website To Plan (POST /plans/subscription/{websiteID}). _(POST /api/crisp/subscribe/website/to/plan)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_subscribe_website_to_plugin`

Subscribe Website To Plugin (POST /plugins/subscription/{websiteID}). _(POST /api/crisp/subscribe/website/to/plugin)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_test_campaign`

Test A Campaign (POST /website/{websiteID}/campaign/{campaignID}/test). _(POST /api/crisp/test/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_transmit_signaling_on_ongoing_call_session`

Transmit Signaling On Ongoing Call Session (PATCH /website/{websiteID}/conversation/{sessionID}/call/{callID}). _(POST /api/crisp/transmit/signaling/on/ongoing/call/session)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `callID` | string | Sim | Path param "callID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_unlink_operator_from_website`

Unlink Operator From Website (DELETE /website/{websiteID}/operator/{userID}). _(POST /api/crisp/unlink/operator/from/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `userID` | string | Sim | Path param "userID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_unpublish_helpdesk_locale_article`

Unpublish Helpdesk Locale Article (POST /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/unpublish). _(POST /api/crisp/unpublish/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_unsubscribe_plan_from_website`

Unsubscribe Plan From Website (DELETE /plans/subscription/{websiteID}). _(POST /api/crisp/unsubscribe/plan/from/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_unsubscribe_plugin_from_website`

Unsubscribe Plugin From Website (DELETE /plugins/subscription/{websiteID}/{pluginID}). _(POST /api/crisp/unsubscribe/plugin/from/website)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_campaign`

Update A Campaign (PATCH /website/{websiteID}/campaign/{campaignID}). _(POST /api/crisp/update/campaign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `campaignID` | string | Sim | Path param "campaignID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_campaign_template`

Update A Campaign Template (PATCH /website/{websiteID}/campaigns/template/{templateID}). _(POST /api/crisp/update/campaign/template)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `templateID` | string | Sim | Path param "templateID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_conversation_inbox`

Update Conversation Inbox (PATCH /website/{websiteID}/conversation/{sessionID}/inbox). _(POST /api/crisp/update/conversation/inbox)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_conversation_metas`

Update Conversation Metas (PATCH /website/{websiteID}/conversation/{sessionID}/meta). _(POST /api/crisp/update/conversation/metas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_conversation_open_state`

Update Conversation Open State (PATCH /website/{websiteID}/conversation/{sessionID}/open). _(POST /api/crisp/update/conversation/open/state)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_helpdesk_locale_article`

Update Helpdesk Locale Article (PATCH /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}). _(POST /api/crisp/update/helpdesk/locale/article)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_helpdesk_locale_article_category`

Update Helpdesk Locale Article Category (PATCH /website/{websiteID}/helpdesk/locale/{locale}/article/{articleId}/category). _(POST /api/crisp/update/helpdesk/locale/article/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `articleId` | string | Sim | Path param "articleId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_helpdesk_locale_category`

Update Helpdesk Locale Category (PATCH /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}). _(POST /api/crisp/update/helpdesk/locale/category)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_helpdesk_locale_section`

Update Helpdesk Locale Section (PATCH /website/{websiteID}/helpdesk/locale/{locale}/category/{categoryId}/section/{sectionId}). _(POST /api/crisp/update/helpdesk/locale/section)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `locale` | string | Sim | Path param "locale" (obrigatório) |
| `categoryId` | string | Sim | Path param "categoryId" (obrigatório) |
| `sectionId` | string | Sim | Path param "sectionId" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_message_in_conversation`

Update A Message In Conversation (PATCH /website/{websiteID}/conversation/{sessionID}/message/{fingerprint}). _(POST /api/crisp/update/message/in/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `fingerprint` | string | Sim | Path param "fingerprint" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_people_data`

Update People Data (PATCH /website/{websiteID}/people/data/{peopleID}). _(POST /api/crisp/update/people/data)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_people_profile`

Update People Profile (PATCH /website/{websiteID}/people/profile/{peopleID}). _(POST /api/crisp/update/people/profile)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_people_subscription_status`

Update People Subscription Status (PATCH /website/{websiteID}/people/subscription/{peopleID}). _(POST /api/crisp/update/people/subscription/status)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `peopleID` | string | Sim | Path param "peopleID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_subscription_settings`

Update Subscription Settings (PATCH /plugins/subscription/{websiteID}/{pluginID}/settings). _(POST /api/crisp/update/subscription/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `pluginID` | string | Sim | Path param "pluginID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_verify_settings`

Update Verify Settings (PATCH /website/{websiteID}/verify/settings). _(POST /api/crisp/update/verify/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_verify_status_for_conversation`

Update Verify Status For Conversation (PATCH /website/{websiteID}/conversation/{sessionID}/verify). _(POST /api/crisp/update/verify/status/for/conversation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `sessionID` | string | Sim | Path param "sessionID" (obrigatório) |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_update_website_settings`

Update Website Settings (PATCH /website/{websiteID}/settings). _(POST /api/crisp/update/website/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `body` | string | Não | Corpo da requisição como JSON string (campos do recurso). Ex. enviar mensagem: {"type":"text","from":"operator","origin":"chat","content":"Olá"}. Campos em docs.crisp.chat. |

#### `crisp_website_get_connect_endpoints`

Get Connect Endpoints (GET /website/{websiteID}/connect/endpoints). _(POST /api/crisp/website/get/connect/endpoints)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas contas Crisp conectadas: id ou label da conexão. Veja crisp_list_accounts. |
| `websiteID` | string | Não | ID do website Crisp. Opcional, usa o website_id da conexão quando omitido. |
| `query` | string | Não | Query params como JSON string OU querystring (filtros + paginação do recurso). Ex.: {"search_query":"joao"}. Campos em docs.crisp.chat. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_crisp` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
