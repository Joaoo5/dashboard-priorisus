# Dashboard PrioriSUS — como colocar no ar

O dashboard é **um único arquivo**: `index.html`. Os 5.571 municípios estão embutidos
dentro dele, então não há backend, banco, build nem dependência de rede. Dá para
testar dando duplo clique no arquivo antes de publicar.

## Publicar na Vercel (sem terminal)

1. Acesse [vercel.com](https://vercel.com) e entre com a conta do GitHub.
2. No topo, clique em **Add New… → Project**.
3. Escolha a opção de deploy manual e **arraste a pasta que contém o `index.html`**
   para a área indicada.
4. Confirme. Em cerca de 30 segundos a Vercel devolve a URL pública
   (algo como `priorisus.vercel.app`).

Não é preciso configurar framework, build command nem output directory — a Vercel
detecta site estático sozinho.

## Publicar pelo terminal (alternativa)

```bash
npm i -g vercel
cd pasta-do-dashboard
vercel --prod
```

## Se preferirem publicar pelo GitHub

Committem o `index.html` numa pasta `dashboard/` do repositório, e na Vercel usem
**Import Git Repository** apontando o *root directory* para essa pasta. A vantagem
é que todo push atualiza o dashboard automaticamente.

## Depois de publicar — checklist

- [ ] Abrir a URL numa aba anônima, para confirmar que está pública
- [ ] Testar o filtro por estado e a busca por município
- [ ] Tirar os prints para o PPT (tela cheia, e um print com um estado filtrado)
- [ ] Colar a URL no slide de arquitetura e no slide de evidências
- [ ] Colar a URL na descrição do vídeo do YouTube

## Como atualizar o dado depois

O `index.html` carrega o dado embutido. Para atualizar depois de rodar o pipeline
de novo, regere o bloco de dados a partir do `OUTPUT/resultado_ipis.csv` e publique
outra vez. O trecho a substituir é a linha que começa com `const RAW =`.

## O que está na tela

- **Quatro indicadores no topo** — recalculam conforme o filtro aplicado.
  O de população em alta prioridade é o número mais forte para o pitch:
  **106,5 milhões de pessoas, 49,9% da população**, vivem em municípios do terço
  mais carente.
- **IPIS médio por estado** — barras ordenadas, com o valor rotulado.
- **Distribuição do índice** — histograma colorido por faixa de prioridade.
- **Ranking completo** — ordenável por qualquer coluna, com busca por nome.
- **Marcação `UBS sem cadastro`** — os 83 municípios cujo índice se apoia apenas
  no déficit de leitos, e o filtro para ocultá-los. Mostrar isso na apresentação
  é um ponto a favor: evidencia que o grupo conhece o limite do próprio dado.
