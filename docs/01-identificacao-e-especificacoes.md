# 1. Identificação e especificações

## Família de modelos

| Modelo | Tela | Chassi | Observação |
|---|---|---|---|
| TV2134(A)SL | 21" | **SL11** (outro projeto!) | Micro Toshiba `A8879CSCFG7C11` + EEPROM 24W16 SMD. **Não é o mesmo chassi** do (B)/(C). Mesmo chassi do TV-2177(A)SL. |
| TV2134(B)SL | 21" slim | **SK11** | Manual de serviço MSTV(3)-071 (temos o PDF). |
| **TV2134(C)SL** | 21" slim | **SK11** | **O seu modelo.** Manual próprio existe (pacote "TV1452/3(P)AV / TV1454(P)SL / TV2134(C)SL / TV2934(C)SL: SK11/SK91"), ainda não baixado, ver [09](09-fontes-e-links.md). |
| TV2134SKY / 2134 Skyworth LPD | 21" | SK11 | Variante citada em fóruns e vídeos. |
| TV2934(B)SL / (C)SL | 29" slim | **SK91** | Mesma placa-base, com AKB e correção E/W. |
| TV1452/1453(P)AV, TV1454(P)SL | 14" | SK11 | Mesma família. |

> "SK" = projeto de origem chinesa (as peças usam nomenclatura chinesa: flyback `BSC25-N1587`,
> transistor `3DD5032`, alto-falante "5P63"). O esquema é assinado pela Semp Toshiba S.A.
> (des. Fernando, 03/ago/2009). O manual do usuário é de 23/09/2009.

**Atenção:** quase toda a documentação pública é do (B)SL. Técnicos em fóruns tratam (B) e (C) como
o mesmo chassi SK11 e citam as mesmas posições de componentes (Q606, C634, D305/D306, C311…),
mas **diferenças entre (B) e (C) não foram confirmadas**, confira sempre a serigrafia da sua placa.

Existem pelo menos duas variantes de placa SK11:
- vertical com **LA78040 / LA78141** (a do esquema oficial);
- vertical com **TDA4865AJ** (circuito diferente; esquema raro, ver [09](09-fontes-e-links.md)).

## Especificações (manual de serviço e manual do usuário)

| Item | Valor |
|---|---|
| Alimentação | 110-220 V~ 50/60 Hz, automática (fonte chaveada full-range) |
| Consumo | 65 W em operação; < 1 W em standby |
| Cinescópio | 21" (53 cm), diagonal visual 51 cm, in-line, tela plana, pescoço slim |
| Sistemas de cor | PAL-M, PAL-N, NTSC (auto ou manual) |
| Padrão de TV | M (525 linhas) / N (625 linhas) |
| Sintonia | PLL sintetizado; VHF 2-13, UHF 14-69, cabo |
| FI | vídeo 45,75 MHz; som 41,25 MHz / 4,5 MHz; croma 42,17 MHz |
| Subportadoras | 3,575611 MHz (PAL-M), 3,582056 MHz (PAL-N), 3,579545 MHz (NTSC) |
| Áudio | 2 × 5 W RMS / 8 Ω, estéreo/SAP (decodificador BTSC) |
| Alto-falantes | 45 × 154 mm, 8 Ω, 10 W (NE 331157) |
| Peso / dimensões | 18,8 kg; 578 × 461 × 332 mm (L×A×P) |
| Controle remoto | CT-7260 (2 pilhas AA, teclas luminosas) |
| Antena | 75 Ω desbalanceada |

## Conexões

- Entrada de antena RF 75 Ω.
- **AV1**: vídeo composto + áudio L/R.
- **AV2 / Vídeo componente (Y Pb Pr)** + áudio L/R ("entrada para DVD").
- Saída de áudio e vídeo (monitor out).
- Painel frontal: CH+/CH-, VOL+/VOL-, MENU (VOL+ e VOL- juntos), chave POWER mecânica.

## Recursos de software

- Menus: INSTALAR, IMAGEM, SOM, AJUSTAR, RELÓGIO. Idiomas: português, inglês, espanhol.
- Modos de imagem: USUÁRIO, SUAVE, PADRÃO, ESPORTE. Modos de som: PADRÃO, MÚSICA, CINEMA, USUÁRIO.
- Closed Caption CC1-CC4 / TXT1-TXT4.
- Bloqueio de canais e de entradas AV. **Senha padrão/mestra: `1984`.**
- Relógio com timer de ligar, desligar e trocar de canal.
- "No Signal Off": desliga após 15 min de tela azul.
- Memória de último estado: se faltar energia com a TV ligada, ela religa sozinha ao voltar.
- Menus somem após 15 s sem comando.

## Limitações conhecidas

- Sem S-Video, sem RGB/SCART, sem entrada frontal.
- Só 15 kHz (480i/240p e 576i/288p). Não aceita 480p/progressivo pela entrada componente.
- Tubo slim de 21": geometria mais difícil de acertar que tubo convencional; pincushion/"efeito taça" é queixa recorrente.
- O 21" **não tem AKB** (ajuste automático de escala de cinza), o cutoff é manual; o 29" tem.
- EEPROM com dados de fábrica específicos por modelo; a Semp não distribuía o arquivo.
