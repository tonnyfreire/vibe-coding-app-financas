Organize suas finanças conversando, do jeito que você fala. Em vez de planilhas e formulários, você escreve no chat algo como *"Gastei R$ 42 no almoço"* ou *"Recebi R$ 1.200 de um freela"* e o app entende, classifica e registra sozinho.

**App no ar:** https://rotina-do-bolso.lovable.app
**Autor:** Tonny Freire

## O que o app faz

- **Cadastro em 1 minuto** — três passos curtos (nome, renda mensal e primeira meta) antes de entrar no chat.
- **Chat que entende linguagem natural** — registra gastos, receitas, cria metas e guarda dinheiro nelas a partir de uma frase simples. Datas relativas ("ontem") viram a data certa.
- **Aprendizado de correções** — se você trocar a categoria de um gasto, o app lembra da próxima vez que a mesma palavra aparecer.
- **Painel** — saldo atual, receitas e despesas do mês, gráfico de "para onde foi seu dinheiro" por categoria e as últimas movimentações.
- **Dicas automáticas** — compara o mês atual com o anterior, avisa quando um gasto subiu, mostra quanto da renda já foi usado e sugere um ritmo diário para completar uma meta.
- **Metas** — progresso em porcentagem, quanto falta e um campo para guardar mais dinheiro (no chat ou na própria tela).
- **Perfil** — editar nome e renda, criar categorias personalizadas e apagar todos os dados para recomeçar.
- **Modo sem internet do assistente** — se a IA falhar, um parser local ainda entende frases como *"Gastei R$ 25 na farmácia"*.

## Como os dados ficam salvos

Tudo (perfil, transações, metas e conversa) fica no `localStorage` do navegador da própria pessoa. Não há login, servidor nem banco de dados — cada aparelho começa do zero e os dados não saem de lá.

## Tecnologias

| Camada | Escolha |
| --- | --- |
| Framework | TanStack Start v1 (React 19, SSR/SSG) |
| Linguagem | TypeScript |
| Estilo | Tailwind CSS v4 + componentes Radix/shadcn |
| Gráficos | Recharts |
| IA | Função de servidor `askAgent` via AI Gateway, com saída em JSON estruturado |
| Dados | `localStorage` via `src/lib/finance.ts` |
| Testes | Vitest + Testing Library |

## Estrutura das telas

| Rota | Tela |
| --- | --- |
| `/boas-vindas` | Cadastro em três passos |
| `/` | Chat com o agente |
| `/painel` | Saldo, resumo do mês, gráfico e dicas |
| `/metas` | Metas, progresso e aportes |
| `/perfil` | Dados, categorias e configurações |

## Rodando no computador

```sh
git clone <url do repositório>
cd <nome-do-repositório>
npm i
npm run dev
```

Outros comandos: `npm run build` (gerar a versão de produção), `npm run lint`, `npm run format`, `npm test`.

## Limites conhecidos

- Sem sincronização entre aparelhos: os dados vivem só no navegador onde foram digitados.
- No modo de emergência (parser local), o chat registra apenas gastos e receitas com valor — metas e perguntas ficam de fora.
- É um MVP de finanças pessoais: sem categorização automática de extratos, contas recorrentes ou relatórios em arquivo.
