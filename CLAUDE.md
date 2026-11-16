# Minha Rota — regras para o Claude

## Idioma
O dono do app **não entende inglês**. Tudo que ele vê deve estar em **português do Brasil** e ser simples: respostas, botões, perguntas e textos do app. Ele costuma ditar por voz e muitas vezes usa o app do Claude no celular.

## O que é
App de celular para viagem de carro (Pernambuco): roteiro de cidades, combustível, hospedagem, outros gastos, quilometragem, mapa final, links para Waze, Google Maps, Booking e Airbnb.

- **App no ar:** https://muciojr1-create.github.io/minha-rota/ (GitHub Pages, branch `main`, pasta raiz; `index.html` da raiz redireciona para `app/`)
- **Código:** `app/index.html` tem o app inteiro (HTML, CSS e JS). Biblioteca de mapa: Leaflet pelo cdnjs.
- Instalável no celular: `app/manifest.webmanifest`, `app/sw.js`, `app/icone-*.png`.

## Os dados do usuário
- Ficam **só no celular** (localStorage, chave `rotaPE.v1`). Nada vai para o repositório.
- Campos novos devem ser opcionais (o `load()` mistura com `def()`), para os dados antigos continuarem funcionando. Nunca renomeie a chave do localStorage.

## O que o usuário pediu e não quer
- **Não gravar o trajeto pelo GPS o tempo todo** (gasta bateria e memória). O caminho é montado ligando os pontos dos lançamentos (função `pontosViagem()`), pelas estradas (OSRM) e no Google Maps.
- Waze, Booking e Airbnb não têm API: a ligação é só por links.

## Como publicar uma mudança
1. Edite `app/index.html`.
2. Aumente o número do `CACHE` em `app/sw.js` (ex.: `minha-rota-v3` → `minha-rota-v4`), senão o celular continua com a versão antiga.
3. Faça commit na branch `main` e push. O GitHub Pages atualiza em cerca de 1 minuto.
4. Diga ao usuário para fechar e abrir o app de novo no celular.

## Serviços usados (grátis, sem chave)
OpenStreetMap (mapa), Nominatim (achar cidades), OSRM (rotas), Overpass (postos e hotéis; às vezes cai), mapa ao vivo do Waze (embed.waze.com).
