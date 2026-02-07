# Workspace da Plataforma WhatsApp Business

Este workspace contém uma arquitetura completa de Agentes e Skills projetada para gerenciar operações profissionais na Plataforma WhatsApp Business (Cloud API). Ele cobre desde campanhas de marketing otimizadas até vendas complexas com Catálogo e pagamentos via PIX/Boleto no Brasil.

## 🎯 Objetivo
Fornecer um conjunto de ferramentas e personas de IA (Agentes) capazes de orquestrar uma operação de WhatsApp de ponta a ponta, seguindo rigorosamente as políticas oficiais da Meta, modelos de precificação e melhores práticas de engenharia.

## 🤖 Agentes Disponíveis
Os agentes são "personas" especializadas que você pode ativar para executar tarefas complexas.

| Agente | Arquivo | Responsabilidade |
| :--- | :--- | :--- |
| **Marketing Campaign Manager** | `agents/marketing_campaign_manager.md` | Estratégia de campanhas, criação de templates ricos (Carrossel, Ofertas Limitadas) e otimização de ROI. |
| **Commerce & Sales Lead** | `agents/commerce_sales_lead.md` | Gestão de Catálogo, Mensagens Multi-Produto (MPM) e processamento de pedidos (PIX/Boleto). |
| **Platform Architect** | `agents/platform_architect.md` | Segurança (HMAC), Infraestrutura de Webhooks, Monitoramento de Qualidade e Estado (Redis). |

## 🛠️ Skills (Ferramentas Procedurais)
As skills são ferramentas técnicas que os agentes utilizam.

- **`whatsapp-marketing-manager`**: Dispara campanhas otimizadas (`/marketing_messages`), gerencia pacing e analisa métricas.
- **`whatsapp-template-manager`**: Cria e valida templates (Marketing, Utilidade, Autenticação). Inclui script de automação `template.sh`.
- **`whatsapp-webhook-handler`**: Implementação de referência para receber e processar eventos (mensagens, status, alertas).
- **`whatsapp-catalog-manager`**: Sincroniza inventário e envia mensagens de produto.
- **`whatsapp-payment-br`**: Formata payloads de pagamento específicos para o Brasil (PIX Copia e Cola, Boleto).

## 🚀 Implementação de Referência (Node.js)
Este workspace inclui uma implementação "Gold Standard" de um servidor webhook em Node.js, baseada na documentação oficial e nos exemplos da Meta.

**Localização:** `skills/whatsapp-webhook-handler/assets/`

- **`server/app.js`**: Servidor Express.js configurado com validação de assinatura `X-Hub-Signature-256`.
- **`services/graph-api.js`**: Classe para chamadas à API (envio de mensagens, templates).
- **`services/conversation.js`**: Lógica de negócios para responder a eventos.
- **`services/redis.js`**: Camada de cache para idempotência e rastreamento de estado.

### Integração com Outras Linguagens (PHP, Python, etc.)
Embora a referência esteja em Node.js, os **conceitos** são universais e devem ser aplicados em qualquer linguagem (PHP, Python, Go, etc.).

## 🇧🇷 Pagamentos no Brasil (PIX/Boleto)
O fluxo de pagamentos é gerenciado pelo agente **Commerce & Sales Lead**.
*   **PIX**: O payload `pix_dynamic_code` deve conter o código gerado pelo seu PSP (Payment Service Provider). O WhatsApp apenas exibe o código para o usuário copiar.
*   **Conciliação**: O campo `reference_id` no pedido é a chave para ligar o webhook do WhatsApp com o webhook do seu Banco/PSP.

## 🔮 Implementações Futuras
Estamos expandindo as capacidades deste workspace para incluir:
- **API de Ligações**: Suporte para chamadas de voz iniciadas por templates de permissão.
- **API de Grupos**: Gestão programática de grupos (criação, adição de membros, envio de mensagens em grupo) via Cloud API.

## ⚠️ Problemas Comuns e Soluções
Consulte as seções de `Troubleshooting` no documento `docs/mental_map.md` para lidar com quedas de qualidade (Quality Score) e falhas de webhooks.

## 📚 Documentação Oficial Utilizada
Este projeto foi construído com base na leitura extensiva da documentação oficial da Meta (Fevereiro 2026).