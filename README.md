# Método Hakari — Landing de vendas (España)

No ar em **lp.metodohakari.com** (Cloudflare Pages, `pages_build_output_dir = "."`).

## Layout atual — versão PROFISSIONAL (rosé/vinho)

`index.html` — página B2B para esteticistas/cosmetólogas. Paleta rosa claro + vinho
(`--accent:#b03a5b`), Playfair Display + Montserrat, coluna de 780px.

Estrutura: anúncio topo → hero (logo + headline + **carrossel antes/depois**) → selos de
confiança → números → dor → o que é o método → 6 motivos → 2 vídeos demonstrativos →
antes & depois → 5 técnicas → anatomia facial → comparativo com/sem método → sobre a
Juliana → materiais inclusos → bônus → oferta (27€) → garantia 7 dias → vídeo depoimento
+ 3 depoimentos → FAQ → CTA final → barra sticky.

### Assets

- `img/` — todas as imagens da página (extraídas dos base64 do layout original; o HTML
  saiu de 815 KB para ~37 KB).
- `videos/` — `hakari-demo-1.mp4`, `hakari-demo-2.mp4` (aulas demonstrativas) e
  `hakari-testimonio-es.mp4` (depoimento vertical). Transcodificados de HEVC para H.264
  (o Chrome não reproduz HEVC).
- O **carrossel da hero** (`#hkSlides`) é o único elemento herdado do layout anterior e
  carrega de `esp.metodohakari.com/img/full-1..5.webp`.

### Checkout

Um único ponto de verdade: a const `HOTMART_URL` no script do fim do `index.html`.
Os 4 CTAs têm `data-checkout` e o guard `hkEnsureOff()` reinjeta o `off=` que o
server-GTM (`api.metodohakari.com`) remove do href no load.

> **PENDENTE**: a página anuncia **27€** mas ainda aponta para a oferta `off=jlhrnwtg`
> (Espanha, 37€). Trocar `HOTMART_URL` pela URL da oferta nova de 27€.

### Tracking

Pixel UTMify (`pixelId 6a28bee1f8a67ee4536fb161`) + `utms/latest.js` no `<head>`, e o
container server-GTM `api.metodohakari.com` logo após o `<body>`.

## Arquivos legados (layout antigo, dourado/claro)

`version-mauve.html` e `version-nude.html` — variações de paleta do layout anterior.
`img/dep-elena|marta|sofia|lucia.png` — screenshots de depoimentos que só o layout antigo
usava. Nada disso é referenciado pelo `index.html` atual.

## Publicar

Cloudflare Pages → Connect to Git (este repo) ou Direct Upload desta pasta.
