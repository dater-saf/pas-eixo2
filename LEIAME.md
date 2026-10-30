# Formulário de Monitoramento – Eixo 2 ATER e Crédito | PAS Nordeste

Arquivos:
- `index.html` – o formulário (página única, sem dependências; publicar no GitHub Pages)
- `Code.gs` – script que grava as respostas numa planilha Google

## Publicação (≈15 min)

1. **Planilha**: crie uma planilha Google (ex.: "PAS NE – Eixo 2 – Monitoramento").
2. **Script**: na planilha, *Extensões > Apps Script*. Apague o conteúdo e cole o `Code.gs`. Salve.
3. **Implantar**: *Implantar > Nova implantação > App da Web*
   - Executar como: **Eu**
   - Quem pode acessar: **Qualquer pessoa**
   - Autorize e copie a URL (termina em `/exec`). Abrindo-a no navegador deve aparecer `{"ok":true,...}`.
4. **Ligar o formulário**: no `index.html`, preencha `ENDPOINT: '...'` com essa URL.
5. **Publicar**: suba o `index.html` num repositório (ex.: `dater-saf/pas-eixo2`) e ative o GitHub Pages.
6. **Teste**: envie uma resposta fictícia e confira as abas criadas. Depois apague as linhas de teste.

Com `ENDPOINT` vazio, o formulário funciona em **modo de teste**: valida tudo e mostra os dados que seriam enviados, sem gravar nada.

## O que fica na planilha

| Aba | Conteúdo |
|---|---|
| `Respostas` | Um registro por envio, com protocolo e data/hora. Histórico completo. |
| `Projetos` | Um registro por projeto indutor de cada envio (etapas, fontes, papel de FIDA/GIZ/IICA/BM). |
| `Situacao_por_ciclo` | Último envio de cada estado em cada ciclo – base para comparar a evolução. |

## Painel (`painel.html`)

1. Substitua o `Code.gs` da planilha pela versão nova e reimplante: *Implantar > Gerenciar implantações > editar (lápis) > Versão: Nova versão > Implantar*. A URL continua a mesma.
2. No `painel.html`, preencha `ENDPOINT` com a mesma URL do formulário.
3. Publique no mesmo repositório (ex.: `.../pas-eixo2/painel.html`).

O painel consulta a planilha a cada minuto (`INTERVALO_MIN`) e redesenha quando há envio novo; também atualiza ao voltar para a aba. Correções feitas à mão na aba `Respostas` também aparecem.
Nome e e-mail dos pontos focais **não** são publicados pelo endereço do painel. Os demais dados ficam acessíveis a quem tiver o link.

## Ajustes rápidos no `index.html` (bloco CONFIGURAÇÃO / LISTAS)

- `PERIODICIDADE`: `'semestral'` (2026-S2…) ou `'trimestral'` (2026-T4…).
- `PROJETOS`: lista de Projetos Indutores (atualizar após validação do Catálogo).
- Ao alterar perguntas, suba a `VERSAO` – ela é gravada em cada envio.

## Para conferir antes de divulgar

- Critério comum de "rede constituída" (pode entrar no texto de ajuda da pergunta 6).
- Lista validada de Projetos Indutores (no slide, "Pronaf Mais Alimentos" aparece duplicado).
- Se houver restrição institucional ao uso de Google Sheets, só o `ENDPOINT` precisa mudar.
