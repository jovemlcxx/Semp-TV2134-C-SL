# 9. Fontes, links e o que falta baixar

Coleta feita em 10/11/2026, com buscas em português, inglês, espanhol, russo e chinês.
Praticamente todo o conhecimento sobre este chassi está **em português** (produto exclusivo do Brasil); as buscas em
outros idiomas só renderam material genérico sobre o CI TDA12165PS e sobre RGB mod.

## Já está neste repositório

| Arquivo | Origem |
|---|---|
| `manuais/SK11_SK91-…-manual-de-servico.pdf` (14 p., com esquemas SK11 e SK91) | electronica-pt.com (anexo do fórum) |
| `manuais/manual-usuario-2134SL-2934SL.pdf` | images.colombo.com.br |
| `esquemas/*.png` | renderizados do manual de serviço a 300 dpi |
| `fontes/foruns/*.txt` | tópicos e dicas (texto limpo) |
| `videos/transcricoes/*.txt` | 39 vídeos do YouTube (36 com legenda) |
| `datasheets/TL431.pdf` | ti.com |

## ⚠️ Para baixar manualmente (sites bloquearam download automático – Cloudflare/login)

Prioridade alta — é o manual do **seu** modelo:

1. **Pacote TV2134(C)SL / TV2934(C)SL / TV1452‑3(P)AV / TV1454(P)SL – SK11/SK91** (2,1 MB)
   https://www.electronica-pt.com/esquema/tv/toshiba-esquemas-tv/toshiba-tv1452-tv1453-tv1454-tv2134-tv2934-20620/
2. Pacote TV2134(B)SL SK11 / TV2934(B)SL SK91 (3,1 MB, 3 esquemas)
   https://www.electronica-pt.com/esquema/tv/toshiba-esquemas-tv/toshiba-tv2134(b)sl-ch-sk11-tv2934(b)sl-chsk91-14874/
3. **Esquema SK11 com vertical TDA4865AJ** (variante rara)
   https://www.4shared.com/get/CuZR0rQEea/TV2134_ch-SK11.html
   e http://www.4shared.com/office/u8PfrplX/SK11__TV2134_B_SL_-_Esquema_El.htm
4. elektrotanya – "TOSHIBA SK11‑TV‑2134‑2934 SM" (2,5 MB)
   https://elektrotanya.com/toshiba_sk11-tv-2134-2934_sm.rar/download.html
5. eserviceinfo – `semp-toshiba-sk11-sk91.zip`
   https://www.eserviceinfo.com/index.php?what=search2&searchstring=ESQUEMA+DE+TV+SEMP+MOD.2134
6. EletrônicaBR (precisa de cadastro/créditos) – categoria Semp Toshiba
   https://eletronicabr.com/files/category/255-semp-toshiba/
7. Cópias do manual de serviço: [dokumen.tips](https://dokumen.tips/documents/manual-servico-tv-toshiba-tv2134-56d6c1ae0eed2.html),
   [idoc.pub](https://idoc.pub/documents/manual-servico-tv-toshiba-tv2134-qvndwd910glx),
   [Scribd](https://pt.scribd.com/document/481297663/SK11-SK91-TV2134-B-SL-TV2934-B-SL-Manual-de-Servico-pdf)

Coloque o que baixar em `manuais/`.

### Datasheets a baixar (buscar pelo nome em alldatasheet.com / datasheetspdf.com)

TDA12165PS (ou família TDA120x1/TDA121xx "UOC‑TOP" – NXP; datasheet completo é raro), STR‑W6554A (Sanken, família STR‑W6500),
LA78040 / LA78141 (Sanyo), TDA4865AJ (Philips), TDA8944J (Philips), TDA9850 (Philips), 24C08, HEF4052, 2SD2553 (Toshiba),
BY228, RU4B/RU3AM/RU3YX (Sanken), S8050, 2SC1815, 2SA1015, 2SA1013, BF422/BF423.

## Fóruns e bases consultadas

- Eletrônica2002: [2134(C)SL batendo relé](https://eletronica2002.forumeiros.com/t205225-tv-semp-toshiba-modelo-tv-2134csl-nao-liga-batendo-releresolvido) ·
  [2134csl bate relé](https://eletronica2002.forumeiros.com/t209524-resolvidotv-semp-toshiba-2134csl-bate-rele-mas-nao-liga) ·
  [imagem sem brilho](https://eletronica2002.forumeiros.com/t157799-encerradotv-semp-2134b-sl-sk-11-imagem-sem-brilho) ·
  [esquema TDA4865AJ](https://eletronica2002.forumeiros.com/t210480-esquema-tv-semp-mod-tv2134-b-sl-sk-11-que-use-tda4865aj) ·
  [arquivo de EEPROM](https://eletronica2002.forumeiros.com/t41012-arquivo-de-eprom-toshiba-modelo-tv2134bsl-chass-sk11) ·
  [não desliga pelo controle](https://eletronica2002.forumeiros.com/t181312-tv-semp-toshiba-tv2134-sk11-nao-desliga-pelo-controle-remoto-e-ruido-na-fonte)
- TecTonny: [2134(B)SL não liga](https://www.tectonny.com.br/forum/html.php?topic=52792.0) ·
  [2134(A)SL sem contraste/EEPROM](https://www.tectonny.com.br/forum/html.php?topic=31447.0)
- Clube do Hardware: [2134 em proteção](https://www.clubedohardware.com.br/forums/topic/1042182-tv-marca-semp-toshiba-modelo-2134-n%C3%A3o-liga-em-modo-de-prote%C3%A7%C3%A3o/) ·
  [3 TVs 2134 SL](https://www.clubedohardware.com.br/forums/topic/1069557-tv-2134-sl-semp/)
- electronica‑pt: [dicas de reparação](https://www.electronica-pt.com/reparacao.php?ref=SK11) (use o campo "Modelo": SK11, SK91, 2134, 2934) ·
  [modos de serviço Toshiba](https://www.electronica-pt.com/service-mode?chassis=&marca=toshiba&page=2)
- EletrônicaBR: [pedido de esquema 2134(B)SL](https://eletronicabr.com/forums/topic/39256-preciso-esquema-semp-tv-2134-b-sl-sk-1/)
- ForumJReletronica2001 (Tapatalk, bloqueou acesso): [2134(A)SL modo de serviço](https://www.tapatalk.com/groups/forumjreletronica2001/semp-toshiba-tv2134-a-sl-sl11-como-entrar-no-modo--t77272.html)
- Blog: [TV2134SKY SK11 – dicas](https://wwwcarloseletronica.blogspot.com/2012/02/tv-semp-mod-tv2134sky-sk11-dicas-de.html)
- shmups (inglês): [TV RGB mod thread p.130 – tentativa num 2134(B)SL](https://shmups.system11.org/viewtopic.php?t=56155&start=3870)
- [Modo de serviço de TVs com TDA12165 (genérico, inglês)](https://electronicshelponline.blogspot.com/2019/02/how-to-enter-service-mode-of-tvs-using.html)
- Ficha comercial: [Zoom – TV 2134SL](https://www.zoom.com.br/tv/tv-semp-toshiba-21-crt-tubo-tv-2134sl)
- Vídeos: ver [`videos/README.md`](../videos/README.md)

## Lacunas conhecidas (o que NÃO foi encontrado)

- Manual de serviço específico do **(C)SL** (existe, não baixado – item 1 acima). Diferenças (B)×(C) não confirmadas.
- **Dump de EEPROM 24C08** do 2134(B)/(C)SL. → Faça o da sua.
- Significado dos parâmetros das páginas 4–15 do modo desenvolvimento (só há vídeo mostrando os valores).
- Datasheet completo do TDA12165PS e confirmação de entrada RGB comutável.
- Modelo exato do cinescópio e equivalência de flyback fora os dois de fábrica.
- Tópicos do Tapatalk/JR Eletrônica e downloads do EletrônicaBR (exigem login).
- 3 vídeos sem legenda (ver índice de vídeos) — precisariam de transcrição por áudio.
