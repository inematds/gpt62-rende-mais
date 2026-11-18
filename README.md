# GPT-6.2 rende mais

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

[![GPT-6.2 rende mais](guia/assets/banner.jpg)](https://inematds.github.io/gpt62-rende-mais/guia/)

## O que é

GPT-6.2 rende mais é uma coleção viva de dicas para usar melhor o Astra e o Sol, os modelos novos da OpenAI. Serve para quem delega trabalho à IA e quer menos paradas e menos surpresas. Cada dica diz o que fazer, para que tipo de uso serve e, quando faz sentido, traz um texto pronto para colar. A base são as publicações oficiais da OpenAI, e novas dicas entram conforme forem conferidas. É só ler e copiar.

## 📖 Guia

**https://inematds.github.io/gpt62-rende-mais/guia/**

As dicas estão em [`DICAS.md`](DICAS.md) e os textos prontos, em [`prompts/`](prompts/).

## Peça para a sua IA analisar o seu caso

```text
Leia as dicas em https://github.com/inematds/gpt62-rende-mais/blob/main/DICAS.md. Depois olhe como eu uso a IA aqui, incluindo as instruções que já existem, e me responda em linguagem simples: 1. Quais dicas resolvem um problema real meu? 2. Alguma instrução minha atrapalha o GPT-6.2? 3. O que você mudaria primeiro? Não mude nada ainda. Se não conseguir abrir o link ou ver as minhas instruções, diga o que devo colar aqui. Mostre o plano e espere eu dizer sim.
```

## Baseado em publicações da OpenAI

- [Using GPT-6.2](https://developers.openai.com/api/docs/guides/latest-model/gpt-6.2-astra): comportamento, prompts, esforço e migração.
- [GPT-6.2 System Card](https://deploymentsafety.openai.com/gpt-6-2-astra-sol): omissão de obstáculos (22,28% no GPT-6.2 Astra e 11,09% no GPT-6 Astra, em tarefas de programação preparadas para provocar o erro; não indica necessariamente a taxa no uso real) e efeito do prompt do Codex.
- [Rethinking skills and prompts for GPT-6 Astra](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra): escrito para a versão anterior; aqui entra como dica para testar.

Conferido em 18/11/2026. Os textos de `prompts/` foram escritos por nós.

---

## Instalação técnica

Não há nada para instalar: copie o texto de `prompts/` para o seu pedido, `AGENTS.md` ou prompt de sistema.

Ao migrar uma integração, a documentação oficial pede para conferir:

| Item | O que fazer |
|---|---|
| Modelo | `gpt-6.2-astra` ou `gpt-6.2-sol` |
| Esforço | começar em `medium`; quem usa `none` ou `minimal` passa para `low` |
| Ferramentas | usar a Responses API |
| Parâmetros | remover `temperature`, `top_p` e `top_logprobs`; em Chat Completions, também `logprobs`; em Responses, tirar `message.output_text.logprobs` de `include` |
| Raciocínio | não editar o início da conversa entre respostas |
| Cache | vindo do GPT-5.5 ou anterior, trocar `prompt_cache_retention` por `prompt_cache_options.ttl` = `"30m"` |

Para repetir o teste, na pasta do projeto e com o Codex CLI autenticado pela assinatura (`3` gera 12 execuções; o script só guarda as respostas, e a classificação é feita lendo cada uma):

```bash
teste/medir_bloqueio.sh 3 teste/nova-rodada
```

O resultado de 18/11/2026 está em [`teste/PROVA.md`](teste/PROVA.md).

## O processo, do início ao fim

🧠 = pessoa com agente · ⚙️ = script · 🤖 = agente de IA pela assinatura

| # | Passo | Comando / o que acontece | Quem |
|---|---|---|---|
| 1 | Chega uma dica | issue no GitHub | comunidade |
| 2 | Conferir | ler a publicação oficial da OpenAI ou rodar um teste próprio; blogs de terceiros, vídeos e redes não entram como fonte | 🧠 |
| 3 | Registrar | acrescentar em `DICAS.md`, com data e situação; texto novo em `prompts/` | 🧠 |
| 4 | Testar, se couber | `teste/medir_bloqueio.sh 3 teste/nova-rodada` ou um teste novo em `teste/` | ⚙️ / 🤖 |
| 5 | Atualizar o guia | editar `guia/index.html` e refazer `guia/en/` e `guia/es/` | 🧠 / 🤖 |
| 6 | Revisar | um revisor que não escreveu a mudança lê o guia | 🤖 |
| 7 | Publicar | commit + push; o GitHub Pages publica sozinho | 🧠 |
| 8 | Divulgar, se for novidade grande | avisar no portal INEMA.CLUB e no grupo INEMA.LLMS | 🧠 |

## Licença

MIT.
