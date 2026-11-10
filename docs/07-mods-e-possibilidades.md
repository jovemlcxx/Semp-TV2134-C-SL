# 7. Mods, recursos ocultos e possibilidades

> ⚠️ CRT = até ~25 kV no anodo, 114-180 V na placa e primário **não isolado**. Qualquer mod exige descarregar o tubo e
> C607, e conhecimento de bancada. Chassi "quente" no primário: use transformador isolador.

## O que a TV já entrega (sem mod)

- **Entrada componente YPbPr em 15 kHz**: é a melhor entrada desta TV. Aceita 480i e, na prática de CRTs de 15 kHz,
  240p (consoles antigos via transcoder). PS2, Wii, Xbox, PSP, DVD: cabo componente direto.
- Para fontes **RGB** (SNES/Mega/Saturn/PS1 via SCART, MiSTer, Raspberry Pi/RGB-Pi): use um **transcoder RGB→YPbPr**
  externo. É a rota sem solda e de qualidade praticamente igual a um RGB mod.
- Composto em AV1.
- PAL-M/PAL-N/NTSC selecionáveis manualmente (útil para consoles NTSC e PAL-M brasileiros). **Não tem PAL 50 Hz europeu
  com subportadora 4,43 MHz** segundo o manual (lista só M/N/NTSC).

## RGB mod: estado do conhecimento

- No esquema, os pinos **49 (PB), 50 (Y), 51 (PR)** do TDA12165PS são a entrada componente. A serigrafia da placa também
  marca essa entrada como RGB (relato no shmups, usuário Eddyiori, jun/2021, tentando modificar um 2134(B)SL).
- Os pinos **27 (FBL: fast blanking)** e **30 (SCART)** existem no CI mas estão **desconectados**.
- Na família UOC da Philips/NXP, a entrada YPbPr pode ser comutada para RGB por software (I²C); em chassis de outras marcas
  o RGB aparece bloqueado pelo firmware. **Ninguém documentou um RGB mod concluído neste chassi.** O tópico do shmups
  ficou sem conclusão ("blanking is probably FBL").
- Caminhos a investigar (hipóteses, não testadas):
  1. Procurar no **modo desenvolvimento** (páginas 4-15) um bit que troque YPbPr↔RGB na entrada AV2. Há bits que
     habilitam/desabilitam AV1 e AV2 na página 13 (visto em vídeo).
  2. Injeção no OSD **não se aplica**: o OSD é interno ao UOC (não há linhas RGB de OSD externas para "sequestrar").
  3. Injeção direta nos amplificadores RGB da placa do tubo é possível em teoria, mas perde brilho/contraste/blanking do UOC,
     não recomendado.
- **Recomendação:** transcoder RGB→YPbPr. Mesmo resultado prático, zero risco para a TV.

## S-Video

Não há entrada. O UOC tem pino CVBS2 (62) livre, mas não há indicação no esquema de entrada de croma separada
habilitada. Um adaptador S-Video→componente/composto externo é a saída.

## Ajustes finos pelo modo de serviço (o "mod" mais útil)

- Geometria completa (HPOS, WID, VCEN, VPOS, HIT, VLIN, DPC, KEY, CNRT, CNRB, HPAR, HBOW).
- Escala de cinza/temperatura de cor (RC/GC/BC cutoff, GD/BD drive).
- Sub-brilho; AGC.
- Reduzir overscan para jogos (WID/HIT), anote os valores originais.
- Ver [04](04-modo-de-servico.md).

## Melhorias de confiabilidade ("mods" de manutenção)

- Trocar Q606 por BD139 com pequeno dissipador (ponto fraco nº 1).
- Recap da fonte e do vertical com 105 °C/baixa ESR; C634/C311 com tensão maior (200-250 V).
- R633 por 220k 1% filme metálico.
- Recolar o ímã da bobina de linearidade com cola adequada.
- Ressoldar chopper, flyback, driver, conectores e CI vertical.
- Backup da EEPROM 24C08.

## Áudio

- Saída 2×5 W BTL (TDA8944). **Não ligar fone/saída de linha direto nos alto-falantes (BTL, sem terra comum).**
- Há saída de áudio/vídeo traseira (monitor out) para amplificador externo.
- Estéreo/SAP por BTSC (TDA9850), irrelevante após o fim da TV analógica.

## TV analógica desligada: usos atuais

- Conversor digital (ISDB-T) via composto ou componente.
- Retro games (uso mais nobre para um CRT de 15 kHz com componente).
- Sem sinal, a TV desliga em 15 min ("No Signal Off"), só afeta o modo TV/antena com tela azul.

## Limites físicos

- Só 15,7 kHz horizontal: nada de 480p/VGA/31 kHz.
- Tubo slim: foco e convergência nos cantos piores que tubo convencional; geometria sensível à tensão do +B.
- Sem AKB no 21": a escala de cinza deriva com o envelhecimento do tubo e precisa de reajuste manual.
