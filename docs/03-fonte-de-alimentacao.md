# 3. Fonte de alimentação (SK11)

> ⚠️ O lado primário **não é isolado da rede**. Use transformador isolador. O capacitor C607 (220 µF/400 V)
> fica carregado com ~170-310 V mesmo com a TV desligada.

## Primário

| Posição | Valor | Função |
|---|---|---|
| F601 | T3,15 A / 250 V | Fusível |
| L601, L602, C601-C603 (0,1 µ X2), R601/SR601 2M2 | | Filtro de linha |
| PTC601 9 Ω + bobina H603 + RL601 | | Desmagnetização |
| D601-D604 | 4 diodos discretos ("2008" no esquema; TA20-08 na lista de peças) com C604/C605 4n7/1 kV | Retificação |
| R606 | NTC 5 Ω | Limitador de surto |
| **C607** | **220 µF / 400 V** | Filtro principal |
| **IC601** | **STR-W6554A** | Chaveador |
| R602/R603 | 68k + 68k | Partida |
| D606 BA158, R607 22 Ω, **C609 10 µF** | | Alimentação VCC (pino 4) |
| ZD602 20 V (18 V em alguma versão), R608 6k8 | | Limite de VCC / quase-ressonância |
| R605 100k, C606 2200 p/2 kV, D605 BA159 | | Snubber |
| **R609 36k** (39k em alguma versão), R610 220 Ω, C611 0,1 µ, C612 820 p | | Realimentação / detecção de sobrecorrente |
| C613 1000 p/2 kV | | Ressonância no dreno |
| C614 2n2/400 Vca, R611 8M2 | | Acoplamento primário-secundário |

### Tensões do IC601 (rede 120 Vca)

| Pino | Função | Ligado | Standby |
|---|---|---|---|
| 1 | D (dreno) | 155 V | 165 V |
| 2 | - | - | - |
| 3 | S/GND | 0 | 0 |
| 4 | VCC | 18,5 V | 13,8 V |
| 5 | ADJ (OCP/BD) | 3,7 V | 0 V |
| 6 | FB | 1,6 V | 12 V |
| 7 | BD | 0 V | 0 V |

## Secundário

| Linha | Ligado | Standby | Retificador / filtro | Uso |
|---|---|---|---|---|
| **+B** | **114 V** | 53 V | D614 RU3AM, **C634**, L306 100 µH, **C311 47 µ/160 V** | Flyback pino 2 |
| +12 V | 12 V | 2,1 V | R635 0,33 Ω, D612 BYW36, C636 1000 µ | Geral, relé |
| +12VS | 12 V | - | R637 0,22 Ω, D610 RU3YX, **C628 1000 µ** | Áudio (TDA8944) |
| (linha baixa) | ~5,8 V stby | | D613 BA158, C635 330 µ/50 V, D626 BA158 | Alimenta os reguladores em standby |
| +8 V | 8 V | | R631 + R743 (51 Ω), ZD709 8V2, C709 100 µ | UOC pino 3 |
| **+5 V** | 5 V | | **Q606 S8050**, ZD604 5V6, R627-R629, C625 100 µ | UOC pinos 2 e 54 |
| +5V1 | 5,1 V | 5,1 V | R625 680 Ω, ZD707 5V1, C724 100 µ | Standby: EEPROM, IR |
| **+3V3** | 3,3 V | 3,3 V | **Q602 C1815**, Q603 A1015, ZD603 3V9, C621 1000 µ, C622 470 µ, J218 10 µH, C238 100 µ | Micro (UOC) |
| +180 V | 180 V | - | do flyback (pino 10) | Placa do tubo |
| ±16 V | ±16 V | - | do flyback (pinos 3/4) | Vertical |

`C619 1000 µF` filtra a linha baixa que alimenta Q604.

## Malha de regulação do +B

`+B → R633 (220k) → nó de 2,5 V → R617 (4k7) + R618 (150 Ω) → massa`, com **Q601 TL431**, R614 2k2, R615 4k7,
C617/C618 1 nF e o optoacoplador **IC602**. O manual marca R617/R618 como "+B ADJ" (ajuste por valor de resistor;
não há trimpot).

**Regra de bancada (fóruns):** qualquer pequena alteração em R633, R617, R618, R614 ou R615 desloca o +B.
+B alto (120-150 V) aciona a proteção e a TV fica "batendo relé".

## Standby

O pino 38 do UOC vai a 0 V para ligar. Em espera (~0,7 V na base de Q605), Q605 conduz e, via ZD605 3V6 + D609 +
Q604 (A1013), força o opto e derruba a fonte para o modo de baixo consumo.

## Valores de referência para diagnóstico rápido

| Medir | Esperado | Se errado |
|---|---|---|
| +B em C634 (standby) | ~53 V | fonte/primário |
| +B em C634 (ligado) | 114 V | > 120 V: R633/R617/R618/TL431/opto. Cai a ~40 V ao ligar: C634, C311, flyback, C303, D302 |
| +5 V (emissor Q606) | 5,0 V | Q606, ZD604 |
| +3V3 | 3,3 V | Q602, ZD603 |
| VCC IC601 pino 4 | 18,5 V | 14 V → C609, D606 |
| ±16 V no IC301 | só com horizontal ativo | D305/D306, R308/R309 |
| +180 V | só com horizontal ativo | D307, R306, C329 |
