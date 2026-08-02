---
description: Analisa vídeo(s) viral(is) mostrando o que faz cada parte funcionar, quais princípios estão aplicados e o que dá pra aprender. Cole um ou mais links.
---

# Analisar Vídeo

## Trigger

Usuário cola link(s) de vídeo ou pede para analisar conteúdo.

## VERIFICAÇÃO DE AMBIENTE (PRIMEIRO PASSO — OBRIGATÓRIO)

Antes de qualquer coisa, verificar se a rede tem acesso externo:

```bash
curl -s --max-time 5 -o /dev/null -w "%{http_code}" "https://api.apify.com" 2>&1
```

**Se retornar "Host not in allowlist" ou falhar:** esta sessão está rodando num container remoto sem acesso ao TikTok/Instagram/YouTube/Apify. NÃO tente fazer chamadas de rede — elas vão falhar.

Nesse caso, responder IMEDIATAMENTE em português:

> **Sofia não consegue acessar vídeos nesta sessão.**
>
> Esta sessão do Claude Code roda num servidor remoto que não tem acesso ao TikTok, Instagram ou YouTube.
>
> **Para analisar agora, escolha uma opção:**
>
> **1. Cole o conteúdo aqui** — Abra o vídeo, copie o texto falado (pode ativar a legenda automática no TikTok) e cole aqui. Eu analiso tudo com os princípios de engajamento.
>
> **2. Rode no terminal do seu PC** — Abra o terminal e rode `claude`, aí o acesso à rede funciona normalmente.

Parar aqui. Não tentar extrair dados. Não inventar conteúdo.

## Antes de analisar — pergunte (1-2 perguntas)

Não saia analisando sem saber pra quê:

1. "Por que quer analisar esse vídeo?" (aprender, copiar formato, comparar)
2. "Tem algo específico que te chamou atenção?" (abertura, roteiro, comentários)

Se já ficou claro pelo contexto, pule direto.

## Fluxo

### 1. Pesquisa (agente: pesquisador)
- Transcrição completa
- Top 20 comentários
- Métricas (views, likes, comments)
- Hook isolado

### 2. Análise bloco a bloco (agente: analista-de-principios)

**Formato obrigatório:** roteiro em blockquote, análise embaixo em 1-2 frases. Sempre nomeie o princípio.

```markdown
> "Frase do roteiro"

(Princípio) O que faz e por que funciona. Se fraco: como melhorar.

> "Próxima frase"

(Princípio + Princípio) Comentário curto.
```

**Regras de concisão:**
- Máximo 2 frases por bloco
- Não repita o que a frase diz
- Se não tem nada pra comentar, agrupe com a próxima
- Se algo está fraco ou faltando: diga qual princípio e sugira melhoria

### 3. Insights de comentários (3-4 linhas)
- Reação dominante
- O que mais comentaram e o que isso revela

### 4. Resumão

```markdown
## Resumo
- **Ideia:** [1 frase]
- **Por que funciona:** [1-2 motivos]
- **Ponto mais forte:** [o que carrega]
- **O que dá pra aprender:** [padrão aplicável]
- **Princípios presentes:** [lista curta]
- **Princípios que faltam:** [se relevante]
```

### 5. Salvar
`Sofia/Pesquisas/{canal}/{titulo}/`

### 6. Próximos passos
> "O que quer fazer?
> 1. Escrever um roteiro inspirado nisso (vou te perguntar antes)
> 2. Comparar com outro vídeo
> 3. Salvar padrões na base de conhecimento
> 4. Exportar"

## Múltiplos vídeos

Analisar cada um separado. No final, comparativo em 3-4 linhas:
- O que têm em comum
- Padrão mais forte
