# 6. Peças, alternativas e compatibilidades

Lista completa de reposição (com códigos NE da Semp) em `manuais/lista-de-pecas-SK11-SK91.txt`
(extraída do manual; é do (B)SL — a coluna "MODELO" do original está desalinhada, não confie nela).

## Substituições relatadas por técnicos

| Original | Substituto relatado | Observação |
|---|---|---|
| **Q606 S8050 / BR8050** (reg. 5 V) | BC337 (pinos invertidos em relação ao original), BC547 "ao contrário", **BD135 / BD139** (com dissipador; trocar base/coletor) | BD135/139 é a escolha mais robusta |
| **IC601 STR‑W6554A** | **STR‑W6556A** (usado com sucesso num 2134) | Mesmo encapsulamento/pinagem, versão de maior potência |
| **IC301 LA78040 / LA78141 / UTC78045** | LA78040, LA78041, LA78045, **STV9302**, TDA8172, TDA9302, AN5522; "o mais indicado: **STV9379A**" | Cuidado com CI vertical falsificado (um tópico: o CI novo já veio ruim) |
| **C634** 47 µF/160 V | 100 µF/200–250 V | Maior tensão/capacitância é bem‑vinda |
| **C311** 47 µF/160 V | 47 µF/200–250 V | |
| **C607** 220 µF/400 V | 220–330 µF/450 V | |
| **D304/D305/D306/D307 BA158** | UF4007, FR104, FR107 | Diodos rápidos; **não** usar 1N4007 |
| **D302 BY228** (damper) | BY228 ou equivalente de damper 1,5 kV | |
| **Q301 2SD2553** | 3DD5032 (alternativo de fábrica); equivalentes de saída H com damper (ex.: 2SD2499, 2SD1555 – conferir) | "conferir" = não confirmado em relato |
| **Q302 STK630** | MOSFET tipo IRF630 | Nota de vídeo: "STK630 ou equivalente" |
| **R633 220k** | 220k 1% metal film; um técnico usa 200k para baixar o +B | Prefira o valor original e 1% |
| **Tuner TDQ‑6FT/13F9S** | **TECC1040PG38P** (Samsung, da Philco TP1454) | PG32T perde canais VHF |
| **T302 BSC25‑N1587** | BSC27‑N2 (alternativo de fábrica) | Outros flybacks: sem equivalência confirmada |
| **IC202 24C08** | Qualquer 24C08 (AT24C08, M24C08, 24LC08) | Precisa dos dados → [04](04-modo-de-servico.md) |
| **Q601 TL431** | TL431 / KA431 / EL431 | |
| **IC602** opto | PC817 / EL817 | |
| Q401, Q402, Q602, Q605 2SC1815 | BC547 (pinagem diferente!) | |
| Q603 2SA1015 | BC557 (pinagem diferente!) | |

## Peças de desgaste — kit de recapeamento recomendado

Baseado nos defeitos repetidos em [05](05-defeitos-e-solucoes.md):

| Posição | Valor | Função |
|---|---|---|
| C607 | 220 µF/400 V | Filtro primário |
| C609 | 10 µF/50 V | VCC do STR |
| C634 | 47 µF/160 V (ou 100 µF/200 V) | +B |
| C311 | 47 µF/160 V | +B após L306 |
| C635 | 330 µF/50 V | Linha de standby |
| C636, C628, C621, C619 | 1000 µF/16 V | 12 V, áudio, 3,3 V |
| C622 | 470 µF/16 V | 3,3 V |
| C625 | 100 µF/16 V | 5 V |
| C318, C319 | 1000 µF/25 V | ±16 V vertical |
| C314 | 100 µF/25 V (um relato cita 220 µF/50 V) | Pump vertical |
| C310 | 4,7 µF/50 V | Acoplamento (relato: causa "efeito taça") |
| C329 | 10 µF/250 V | 180 V vídeo |
| C309 | 2,2 µF/250 V | (relato: seco → sem foco) |
| C218, C223 | 10 µF/16 V | Desacoplos do UOC |
| C613 | 1 nF/2 kV cerâmico | Dreno do STR |

Use capacitores 105 °C de baixa ESR na fonte e no vertical.

## Semicondutores para ter em estoque

Q606 (BD139), Q602/Q605/Q401 (2SC1815), Q604 (2SA1013), TL431, PC817, BA158/UF4007 ×6, zeners 5V1/5V6/3V9/8V2,
R308/R309 0,33 Ω fusível, R633 220k 1%, R609 36k, R604 2k2, R602/R603 68k, R224/R225 100k, R325 56k.

## Compatibilidade entre modelos

| Peça | 2134(B)/(C) SK11 | 2934 SK91 | 2134(A) SL11 |
|---|---|---|---|
| Placa principal | base comum | mesma base, valores diferentes no H/EW | **outra placa** |
| IC201 | TDA12165PS (firmware Semp) | idem | Toshiba TMPA8879 |
| EEPROM (dados) | próprios do 21" | **diferentes** | 24W16, incompatível |
| Flyback | BSC25‑N1587 / BSC27‑N2 | outro | outro |
| Fonte | STR‑W6554A, T601 BCK‑35 | STR maior, T601 BCK‑40 | — |
| Controle | CT‑7260 | CT‑7260 | — |

O IC201 é um microcontrolador **mascarado/gravado com o firmware da Semp**: um TDA12165PS de outra marca de TV
não serve como doador; tire de outra placa SK11/SK91.

## Cinescópio

Tubo slim de 21" (pescoço fino, deflexão larga). Um tópico cita teste com tubo **TGDC**; um vídeo cita uma variante "2134 Skyworth LPD"
(LPD = LG.Philips Displays). O modelo exato do tubo está na etiqueta do seu aparelho — **anote em `docs/minha-unidade.md`**.
Tubos slim não são intercambiáveis com tubos convencionais de 21" (yoke e geometria diferentes).

## Datasheets

`datasheets/` — ver a lista e os links em [09](09-fontes-e-links.md).
