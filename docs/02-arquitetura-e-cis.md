# 2. Arquitetura do chassi SK11 e mapa de CIs

Tudo aqui foi lido do esquema oficial do TV2134(B)SL (`esquemas/SK11-TV2134BSL-esquema-completo-300dpi.png`).
Tensões são as impressas no esquema (medidas com rede de 120 Vca).

## Semicondutores principais

| Posição | Peça | Função |
|---|---|---|
| IC201 | **TDA12165PS** (NXP "UOC-TOP", SDIP-64) | Tudo-em-um: microcontrolador + FI + demodulador + croma + deflexão + RGB + OSD/CC |
| IC202 | **24C08** | EEPROM I²C (ajustes de fábrica e de usuário) |
| IC601 | **STR-W6554A** (Sanken) | Fonte chaveada quase-ressonante (controlador + MOSFET) |
| IC602 | Optoacoplador ("T781" no esquema; tipo PC817) | Realimentação da fonte |
| Q601 | **TL431** | Referência / amplificador de erro do +B |
| IC301 | **LA78040** ou **LA78141** (tubo slim) | Saída vertical, alimentação simétrica ±16 V |
| IC401 | **TDA8944** | Amplificador de áudio estéreo BTL (2 × 7 W nominais) |
| IC701 | **4052** | Chave analógica de áudio (TV / AV1 / AV2) |
| IC801 | **TDA9850** | Decodificador BTSC estéreo/SAP |
| IC802 | **78L09** | Regulador 9 V do BTSC |
| Q301 | **2SD2553** (alt. 3DD5032) | Saída horizontal (com damper interno) |
| Q303 | 2SC2482 | Driver horizontal |
| Q401 | 2SC1815 | Acionamento do relé RL601 (desmagnetização) |
| Q602 | 2SC1815 | Regulador dos **3,3 V** do micro |
| Q603 | 2SA1015 | Auxiliar do regulador de 3,3 V |
| Q604 / Q605 | 2SA1013 / 2SC1815 | Comando de standby da fonte (baixa as tensões em espera) |
| Q606 | **S8050** | Regulador dos **+5 V** |
| Q501-Q509 | BF422 / BF423 / 2SC2482 | Amplificadores RGB na placa do tubo |
| X201 | Cristal **24,576 MHz** | Clock do UOC |
| SAW201 | Filtro SAW de FI | |
| T301 | BCT-19G | Trafo driver horizontal |
| T302 | **BSC25-N1587** (alt. BSC27-N2) | Flyback |
| T601 | BCK-35-LF01X-EP | Trafo chopper da fonte |

## Pinagem do IC201: TDA12165PS (com tensões do esquema)

| Pino | Nome | Tensão | Ligação |
|---|---|---|---|
| 1 | IFVO | 1,5 V | R209 100 Ω |
| 2 | VP2 | 5 V | +5V via L202; C216 10 µ, C217 0,1 µ |
| 3 | VCC8V | 8 V | +8V via L201; C215 10 µ, C214 0,1 µ |
| 4 | PLLIF | 2 V | R206 390 Ω + C213 0,1 µ |
| 5 | GND2 | 0 | |
| 6 | DECSDEM | 2,2 V | C218 10 µ |
| 7 | FMDEM OUT | 2,2 V | R208 2k2 → FMDEM (entrada do BTSC TDA9850) |
| 8 | EHTO | 1,6 V | R207 100 Ω, R219 56k (+5V), R218 27k, ZD209 5V6, C212 330 p, proteção/compensação de MAT |
| 9 | AGC | 2,2 V | R116 680 Ω → AGC do tuner; C115 10 n |
| 10 | IREF | 2 V | R205 39k à massa |
| 11 | VSC | 2,4 V | **C219 150 nF** (rampa vertical) |
| 12 / 13 | VIFIN2 / VIFIN1 | 1,9 V | SAW201 |
| 14 | VDRA | 0,5 V | R210 100 Ω, C211 1 n → vertical |
| 15 | VDRB | 0,5 V | R211 100 Ω, C210 1 n → vertical |
| 16 | AVL/EW | 4 V | R212 100 Ω, C220 1 n → EW (usado no 29") |
| 17 | DECBG | 2,3 V | C209 10 µ, C208 100 n |
| 18 | SECPLL | 2,3 V | C221 220 n |
| 19 | GND1 | 0 | |
| 20 | PH1LF | 2,3 V | R204 12k, C207 1,5 µ, C206 6n8 |
| 21 | PH2LF | 2,0 V | C222 10 n |
| 22 | VP1 | 5,2 V | +5V2 via L200; C204 0,1 µ, C205 100 µ |
| 23 | DECDIG | 2,5 V | **C223 10 µ, C224 0,1 µ** |
| 24 / 25 | XTALOUT / XTALIN | 1,8 V | X201 24,576 MHz |
| 26 | SYS | - | não ligado |
| 27 | **FBL** | - | **não ligado** (fast blanking) |
| 28 | LED | 3,9 V | R227 1k → LED |
| 29 | KEY | 3,4 V | R228 100 Ω, ZD203 5V6, C239 10 n → teclado por escada resistiva |
| 30 | **SCART** | - | **não ligado** |
| 31 / 32 | AV1 / AV2 | 5 V | Pull-ups R225/R224 100k (+5V1) → seleção do 4052 |
| 33 | VDDP 3.3V | 3,4 V | +3V3 via L203; C226 10 µ, C227 0,1 µ |
| 34 | SDA | 3,8 V | R221 10 Ω, ZD202 5V6 → EEPROM/tuner/BTSC |
| 35 | SCL | 3,4 V | R222 10 Ω, ZD201 5V6 |
| 36 | WP | 5 V | proteção de escrita da EEPROM |
| 37 | MUTE | 4,6 V | R232 1k |
| 38 | **STANDBY** | 3,3 V em espera / 0 V ligado | R233 3k3 → Q605 |
| 39 | IR | 3,8 V | R231 100 Ω, ZD200 5V1 → receptor IR |
| 40 | VDDC 3.3V | 3,3 V | L204 |
| 41 | GND5 | 0 | |
| 42 | VPE | 3,4 V | R220 10k à massa |
| 43 | VDDA1 3.3V | 2 V (sic) | L205; C228 220 n, C229 100 µ |
| 44 / 45 / 46 | BOUT / GOUT / ROUT | 2,0 V | R234/R235/R236 100 Ω, ZD204-206 8V2 → placa do tubo |
| 47 | IK | 0,9 V | R237 1k à massa (AKB não usado no 21") |
| 48 | BCLIN | 2,2 V | C231 10 µ, R239 1k ← BCL (ABL) |
| 49 | **PB** | 0 V | R240 100 Ω + C235 0,1 µ ← conector componente (R707 75 Ω) |
| 50 | **Y** | 1,4 V | R241 100 Ω + C236 0,1 µ ← conector componente (R705 75 Ω) |
| 51 | **PR** | 1,6 V | R242 100 Ω + C237 0,1 µ ← conector componente (R706 75 Ω) |
| 52 / 53 | YOUT / YSYNC | 1,7 / 2,0 V | C232 0,1 µ entre os dois |
| 54 | VP3 | 5 V | +5V via L206; C233, C234 |
| 55 | GND3 | 0 | |
| 56 | HOUT | 0,5 V | R213 100 Ω, R747 100 Ω, R741 2k2 (+5V) → driver Q303 |
| 57 | FBISO | 0 V | R243 12k, ZD208 5V6 ← AFC do flyback (pino 7) |
| 58 / 59 | LSR / LSL | 3,5 V | R244/R245 1k → TDA8944 |
| 60 | AUDIOIN5R | - | não ligado |
| 61 / 63 | AUDIOIN1R / AUDIOIN1L | 2,2 V | R217/R216 1k ← RS/LS (4052) |
| 62 | CVBS2 | - | não ligado |
| 64 | CVBS4 | 1,4 V | R215 100 Ω ← VIDEO1 (entradas AV) |

Sinal de retorno do vertical no UOC: pulso de 3,8 V a cada 20 ms/16,7 ms (indicado no esquema).

## EEPROM IC202 (24C08)

Pino 5 SDA (3,7 V), pino 6 SCL (3,5 V), pino 7 WP ligado ao pino 36 do UOC, pull-ups R223/R248/R249 3k3 ao +5V1.
C202/C203 33 pF, R202/R203 100 Ω.

## Saída vertical IC301 (LA78040 / LA78141)

| Pino | Função | Tensão |
|---|---|---|
| 1 | VDRB (entrada) | 0,4 V |
| 2 | VCC+ | +16,5 V |
| 3 | PUMP | 13,8 V (C314 100 µ/25 V) |
| 4 | VCC- | -16 V |
| 5 | OUTPUT | 0 V |
| 6 | FLBK | 17 V |
| 7 | VDRA (entrada) | - |

As tensões ±16 V vêm do flyback (pinos 3 e 4) por **D306 / D305 (BA158)** e **R309 / R308 (0,33 Ω fusíveis)**.
Só existem com o horizontal funcionando.

## Estágio horizontal / flyback T302

| Pino | Função |
|---|---|
| 1 | HY: coletor do Q301 |
| 2 | **+B 114 V** |
| 3 | V+ (+16 V do vertical): R309 0,33 Ω, D306 BA158, C322 470 p/500 V |
| 4 | V- (-16 V do vertical): R308 0,33 Ω, D305 |
| 5 | Massa |
| 6 | HT: filamento (R307 3,0 Ω) |
| 7 | AFC: R1 1k, C320 220 p/500 V → pino 57 do UOC |
| 8 | BCL/ABL: R304 1k, R302 5k6 (+8V), C324 0,1 µ, D310 BA158, D309 1N4148 (4,8 V) |
| 10 | +180 V (vídeo): R306 0,18 Ω, D307 BA158, C323 470 p/500 V, **C329 10 µ/250 V** |
| - | HV, FOCUS, G2 (potenciômetros no próprio flyback) |

Outros: C305 3n9/2 kV, C306 7n2/2 kV, C307 4n7/2 kV (sintonia), D302 BY228 (damper), D301 RU4B, C301 22 n,
C303 (correção S), L304 44 µH (linearidade H), C308 680 p/2 kV.

Conector H302 para a placa do tubo: 1 = +180 V, 3 = filamento, 4 = massa do CRT. CN302 = bobinas defletoras (1-2 H, 3-4 V).

## Placa do cinescópio

Amplificadores RGB discretos (BF422/BF423). **C504 (1 nF/2 kV)** fica na linha de G2/screen, em outra
revisão de placa o mesmo capacitor chama-se **C902**.

## Outros blocos

- **Baixo consumo em standby**: o micro (pino 38) comanda Q605/Q604, que derrubam a fonte para modo reduzido
  (o +B cai para ~53 V). O relé RL601, acionado por Q401, comuta a bobina desmagnetizadora (PTC601 9 Ω).
- **Teclado**: chaves SW001-SW004 (CH+, CH-, VOL+, VOL-) em escada resistiva num único pino (KEY).
