# Painel Meta x Realizado

Página única (HTML) que lê as planilhas de vendas exportadas do sistema e compara o realizado de cada cliente com a meta passada pelo supervisor (Geral, IQF e ALP). Monta a mensagem de acompanhamento e abre o WhatsApp com ela pronta.

## O que ele faz
- Lê um ou vários arquivos `.xlsx` (formato "Grupo de Produtos / PRODUTO / CLIENTE / Preço Médio / Volume / Faturamento").
- Soma volume e faturamento totais, IQF e ALP por cliente (ou por arquivo).
- Compara com a meta (digitada ou colada da mensagem do supervisor) e mostra % atingido e quanto falta.
- Gera a mensagem e envia pelo WhatsApp (`wa.me`) ou copia o texto.

## Classificação dos grupos
- **IQF:** grupos com "IQF" no nome.
- **ALP:** batatas, massas, pão de queijo, processados, sanduíche, tilápias (inclui empanada), polenta e mandioca.
- **Fora de IQF e ALP:** o restante (conta apenas no Geral).

Dá para ajustar na própria página, em "Como cada grupo de produtos é classificado". Para mudar a regra padrão, edite `ALP_KEYS` e `classifyDefault` em `index.html`.

## Privacidade
Tudo roda no navegador: as planilhas **não são enviadas a nenhum servidor** e não ficam salvas. Só as metas e preferências ficam no `localStorage` do navegador de quem usa.

> Os valores de meta pré-preenchidos (Box Verona) estão no código. Se o repositório for público, troque-os por valores vazios em `load()` (objeto `d`) ou mantenha o repositório privado.
> Nunca suba as planilhas no repositório (o `.gitignore` já bloqueia `.xlsx`).

## Publicar no GitHub Pages
1. Crie um repositório no GitHub e envie estes arquivos (veja abaixo).
2. Em **Settings → Pages**, em *Build and deployment*, escolha **Deploy from a branch**, branch `main` e pasta `/ (root)`.
3. Aguarde 1–2 minutos. O painel fica em `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

Observação: Pages em repositório privado exige plano pago do GitHub.

## Enviar para o GitHub (terminal)
```bash
cd painel-meta-realizado
git init
git add .
git commit -m "Painel meta x realizado"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/NOME-DO-REPOSITORIO.git
git push -u origin main
```
Sem terminal: no GitHub, **Add file → Upload files** e arraste `index.html`, `README.md`, `.gitignore` e `.nojekyll`.

## Dependências
Carregadas por CDN (precisa de internet): [SheetJS 0.18.5](https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js) e as fontes Bricolage Grotesque e Public Sans (Google Fonts, com fallback do sistema).
