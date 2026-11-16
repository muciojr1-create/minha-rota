# Minha Rota

App de celular para a viagem a Pernambuco: roteiro das cidades, combustível, hospedagem, outros gastos, quilometragem e mapa final.

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `app/index.html` | O aplicativo inteiro (telas, cálculos e estilo) |
| `app/manifest.webmanifest`, `app/sw.js` | Permitem instalar no celular com ícone e abrir sem internet |
| `app/icone-*.png` | Ícones do app (pino com sombrinha de frevo) |

## O que cada aba faz

- **Início**: hodômetro da viagem, total gasto, consumo real (km/l), custo por km, orçamento, calculadora de trecho.
- **Roteiro**: cidades na ordem e noites em cada uma. Calcula a rota, km, tempo, litros e custo de cada trecho, lista os postos no caminho e abre Waze, Booking e Airbnb com as datas certas.
- **Perto**: pelo GPS, postos e hospedagens ao redor, mapa ao vivo do Waze e atalhos para Google Maps, Booking, Airbnb e preços da ANP.
- **Gastos**: abastecimentos, hospedagens e outros gastos (editar e excluir).
- **Mapa**: mapa final com trajeto, rota planejada, pontos de cada gasto e resumo por cidade.
- **Ajustes**: veículo, datas, orçamento, backup e planilha CSV.

## Serviços usados (gratuitos, sem chave)

- Mapas: OpenStreetMap (Leaflet)
- Cidades: Nominatim
- Rotas: OSRM
- Postos e hotéis: Overpass (às vezes fica lento ou fora do ar; o app avisa)
- Waze: só links e o mapa ao vivo. O Waze não deixa outros apps lerem as rotas da conta.

## Rodar no computador

```bash
python -m http.server 8765 --directory app
```

Abra `http://localhost:8765`. Os dados ficam guardados só no navegador/celular onde o app é usado.

O GPS do celular só funciona com o app aberto por **https** (por exemplo, publicado no GitHub Pages).
