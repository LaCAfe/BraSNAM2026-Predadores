# BraSNAM2026-Predadores

Repositório destinado aos artefatos gerados no trabalho entitulado *"From
Bag-of-Words to Reasoning: Comparing Traditional Supervised ML and Zero-Shot
LLMs for Sexual Predator Identification in Brazilian Portuguese"* submetido
ao BraSNAM 2026.

## Artefatos do Prompt 1 (zero-shot)

| Arquivo | Descrição |
|---|---|
| [`prompt1.txt`](prompt1.txt) | Template exato do Prompt 1 (em PT-BR) enviado aos LLMs, e descrição de como o XML de cada conversa foi inserido no `{xml_string}`. Inclui também o procedimento de amostragem e o formato de requisição por provedor. |
| [`conversations_prompt1.xml`](conversations_prompt1.xml) | As 78 conversas usadas no experimento, em XML, ordenadas por `conv_id` crescente. Cada `<conversation>` é o subárvore literal extraído do corpus PAN-12-BR-pt — exatamente o conteúdo substituído em `{xml_string}` no `prompt1.txt`. |
| [`results_prompt1.csv`](results_prompt1.csv) | Saída dos quatro LLMs (Claude Opus 4.6, GPT-5.2, Gemini 3.1 Pro Preview, Grok 4.20) para cada uma das 78 conversas: rótulo previsto, justificativa, eventuais erros de parse/API e timestamp. Total: 312 linhas (78 × 4 modelos). |

## Como reproduzir uma única chamada

1. Pegue o template em `prompt1.txt` (seção "PROMPT TEMPLATE").
2. Escolha um `conv_id` qualquer em `results_prompt1.csv`.
3. Localize a `<conversation id="<conv_id>">` correspondente em
   `conversations_prompt1.xml`.
4. Substitua `{xml_string}` no template pelo subárvore XML completo
   (com a tag `<conversation>` externa).
5. Envie o prompt resultante a qualquer um dos quatro LLMs listados,
   usando o `custom_id`/`key` `p1__<conv_id>`. O modelo deve responder
   exclusivamente com `{"label": "Sim"|"Não", "reason": "..."}`.
