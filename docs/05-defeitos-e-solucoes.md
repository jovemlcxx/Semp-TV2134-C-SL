# 5. Defeitos conhecidos e soluções (chassi SK11 / SK91)

Compilado de ~160 dicas de bancada (electronica-pt), tópicos de fóruns (Eletrônica2002, TecTonny, Clube do Hardware)
e 39 vídeos de técnicos. Textos originais em `fontes/foruns/` e `videos/transcricoes/`.
"(C)" = relato explícito no TV2134(C)SL. "SK91" = relato no 29", que compartilha o projeto.

> São relatos de terceiros, não verificados por nós. Meça antes de trocar. **Sempre confirme o +B (114 V) primeiro.**

## Os 8 culpados clássicos deste chassi

| # | Peça | Por quê |
|---|---|---|
| 1 | **Q606 (S8050 / BR8050)**: regulador de +5 V | "Muito crítico". Com fuga, os 5 V caem para 3-3,9 V e a TV faz de tudo: bate relé, fecha vertical, fecha horizontal, linha vertical, liga/desliga. Técnicos dizem "troque sem medir". |
| 2 | **C634 e C311**: filtros do +B (47 µF/160 V) | Secam. +B oscila/sobe a 130-150 V e corta, ou cai para 40 V ao ligar. |
| 3 | **R633 (220 kΩ)**: amostra do +B | Altera para 240-285 kΩ → +B alto (128-147 V) → proteção, queima vertical. |
| 4 | **D305 / D306 (BA158)**: retificadores do ±16 V do vertical | Abrem ou ficam intermitentes; "medem bons mas estão ruins". Liga/desliga, vertical fechado, efeito taça. |
| 5 | **C318 / C319 (1000 µF/25 V)**: filtros do ±16 V | Estufam. Vertical fechado, não liga. |
| 6 | **R308 / R309 (0,33 Ω fusíveis)** | Abrem quando o CI vertical entra em curto. |
| 7 | **C613 (1 nF/2 kV)** junto ao STR | Carboniza/esquenta: liga e desliga, imagem treme com o volume, fecha horizontal. |
| 8 | **Solda fria** na fonte, horizontal e vertical | Citada em vários vídeos como única causa. Ressoldar chopper, flyback, driver, CI vertical. |

## Não liga / "bate relé" / liga e desliga

| Sintoma | Causa / solução | Fonte |
|---|---|---|
| Bate relé, não liga (C) | **D305 e D306** defeituosos (mediam bons) | E2002 t205225 |
| Bate relé a cada 10 s, +B 130 V (C) | **Saída horizontal Q301 aberta** (após trocar meia fonte à toa) | E2002 t209524 |
| Estala relé, LED pisca, +B sobe a 150 V (C) | **R609 (36k, primário)** alterado para 70k | electronica-pt |
| Liga, desliga e bate relé; C607 fica carregado | **R633 220k** alterado | electronica-pt (vários) |
| +B 120 V | R617/R618 alterados; conferir R615, R633; trocar TL431 | electronica-pt |
| +B 128-150 V e desarma | **C634** seco/aberto (pode usar 100 µF/250 V) | vários |
| +B cai de 114 V para ~40 V ao ligar | **C311**; também C303 (184J) e **D302** em outros aparelhos | Clube do Hardware |
| Fonte com +B alto e VCC do STR em 14 V | Ressoldar/trocar **C609** e diodos junto ao STR | Clube do Hardware |
| Acende LED e apaga; C607 carregado | **R604 (2k2)** junto ao optoacoplador | electronica-pt |
| Pisca LED uma vez, fonte ~200 V caindo | R604 | electronica-pt |
| Fonte a 200 V, LED piscando | **Q604** | electronica-pt |
| Não desliga pelo controle (desliga e religa só com imagem) | **Q604, Q605** | E2002 t181312 |
| Liga e desliga depois de alguns minutos | **R608 (6k8)** junto ao STR | electronica-pt |
| Liga e desliga sozinha | **R218 (27k)** (rede do pino EHTO); ou **C635 (330 µF/50 V)** seco | electronica-pt |
| Liga, funciona, relé bate e aciona desmagnetização | **Q401 (2SC1815)**, trocar sem testar | electronica-pt |
| Bate relé, sem LED; ou LED aceso sem aceitar comando | **ZD202 (5V6, linha SDA)** com fuga; **R248 (3k3)**; **ZD201** | electronica-pt |
| Fonte gera, corta, 3,3 V cai para 0,8 V | **Q602 (C1815)**, "não adianta medir, tem que trocar" | TecTonny 52792 |
| Bate relé 2×, LED apagado, fonte 145 V, 3,3 V em 3,7 V | **IC201** (UOC) | electronica-pt |
| Reinicia, 5 V em 3,6 V mesmo com Q606 novo | **IC801 (BTSC)** em curto puxando os 5 V, soltar jumper J733 para isolar | electronica-pt |
| Liga e desliga, bate relé | R308/R309 alterados + **IC301** queimado | electronica-pt |
| Liga e desliga após 1 min | Q805 (8050) → BD139 (inverter base/coletor) | electronica-pt |
| Controle remoto não funciona | **ZD200 (5V1)** ao lado do UOC | electronica-pt (SK91) |
| Volume vai a zero sozinho / teclado "doido" | **ZD203 (5V6)** na linha KEY com fuga; chaves de volume com fuga | electronica-pt |

## Inoperante / queima fusível

| Sintoma | Causa / solução |
|---|---|
| Queima fusível F601 (T3,15 A) (C) | **D603 e D606/D602** em curto + C607 estufado; STR em curto |
| STR-W6554A em curto / queima na hora | **C607 (220 µF/400-450 V)** aberto/vazio é o causador; trocar junto com a ponte |
| STR em curto + resistor de fio queimado | Trocado por **STR-W6556A** com sucesso |
| Sem standby, C607 carrega e fica | **R602 / R603 (68k)** de partida abertos; **ZD601** em curto (SK91) |
| LED apagado, fonte boa (SK91) | D611 em curto |
| Fonte baixa ~50 V | TL431 (Q601) |
| Fonte não regula / pulsa | Optoacoplador + TL431; trafo chopper com terminal partido (visto no 1454) |

## Vertical

| Sintoma | Causa / solução |
|---|---|
| Vertical fechado (linha horizontal) (C) | **R308** aberto + C318/C319 (1000 µF/25 V) + IC301 |
| Vertical fechado do meio para baixo (C) | **C318** estufado; trocar também **C314** |
| Vertical caindo até o meio da tela (C) | **C219 (150 nF)** no pino VSC do UOC |
| Vertical fechado ~3 cm (C) | CI vertical (na placa (C) vem **UTC78045**) |
| Vertical fechado pela metade, listras brancas em cima | **D304 (BA158)**, diodo do pump (pino 3→6); se persistir, CI vertical |
| Linhas entrelaçadas embaixo "parecendo defletora" (C) | **D305** alterado |
| Imagem escura com manchas / só som e manchas | **D306** ou **D305** aberto |
| Linhas verticais/retraço no topo | **R333 (220 Ω)** ao lado do CI vertical; C636 |
| Queimando CI vertical repetidamente | +B alto (R633) deixa o ±16 V alto |
| Vertical fechado, oscilador interno do UOC sem 60 Hz (SK91) | IC201 |
| Quadro reduzido V e H | C636, C628, C621, C619 (1000 µF/16 V) |

## Horizontal / largura / geometria

| Sintoma | Causa / solução |
|---|---|
| Efeito taça / almofada / "cintura de pilão" | **R325 (56k-68k)** alterado; **Q302 (STK630)**; **C310 (4,7 µF/50 V)**; C304 (SK91) |
| Faixas pretas nas laterais intermitentes | C311 + **Q302** (vídeo "correção no circuito EW") |
| STK630 em curto | efeito inverso: imagem abre demais |
| Imagem fechada nas laterais (C) | **C635 (330 µF/50 V)**; também C636, C309, C325 |
| Vai fechando o horizontal ao ligar | Q606 |
| Queima saída horizontal | **Bobina defletora** em curto; bobina **L301 (790 µH)** ao lado do flyback; C305/C306/C307 abertos |
| Caracteres e imagem duplicando, serrilhado, ruído (C) | **Ímã da bobina de linearidade (L302/L304) descolou e caiu**, recolar um ímã pequeno sobre a bobina |
| Apito agudo | Núcleo de bobina do horizontal descolado; grampo do ferrite do flyback; ressoldar |
| Apito no flyback / zumbido | C311 e C634; C633 rachado (SK91) |
| Imagem esticada na horizontal (SK91) | C301 em curto |
| Imagem serrilhando | Flyback em curto interno |

## Imagem / cor / brilho

| Sintoma | Causa / solução |
|---|---|
| Tela branca/esverdeada com retraço, sem controle de contraste | **C329 (10 µF/250 V: filtro dos 180 V)** esgotado; R525 aberto |
| Imagem sem brilho, fraca | Soquete do cinescópio; **C504 (ou C902) na linha de screen**; flyback |
| Sem foco, ajuste de foco não atua | **C309** seco |
| Tela esverdeada | Q507, Q508, Q509 com fuga (placa do tubo) |
| Imagem azulada | R506 (15k) alterado |
| Toda verde (SK91) | Q503 |
| Embaçada com efeito arco-íris | IC201 |
| Imagem fraca "parecendo tubo" (SK91) | **L301 (790 µH)**, trocar sem medir |
| Sem contraste / geometria e cores malucas | EEPROM corrompida → ver [04](04-modo-de-servico.md) |
| **Letra "M" no canto da tela** | Modo de fábrica ativo: MENU-1-9 e depois a tecla **100** (ou "-/--") do controle |

## Som

| Sintoma | Causa / solução |
|---|---|
| Som some após minutos, chiado, rouco | **R225 / R224 (100k)** abertos (pull-ups AV1/AV2) + C636 |
| Sem áudio total | **R404 (100k) / R405 (75k)** do mute; Q402 (mute), retirar para testar |
| Sem som só em RF | **C218 (10 µF, pino 6 do UOC)**; C718 (10 µF/16 V); R805; CI BTSC |
| Som rouco e chiando | C627 |
| Às vezes sem áudio ou roncando | Filtro de 470-1000 µF da linha de 12 V |
| Sem som com tudo aparentemente bom | Versão com CI equalizador **IC851**: trocar ou fazer o bypass descrito na dica (Q801, R804, R739, R740, J801/J802) |
| Áudio mudo após troca de EEPROM | Bit de MUTE no modo desenvolvimento (página 13) em 1 → pôr 0 |

## Sintonia

- Não sintoniza: resistor do AGC aberto; R106 (10k) ao lado do tuner (SK91).
- Tuner original chinês **TDQ-6FT/13F9S** não se encontra → substituir por **TECC1040PG38P (Samsung)**, o da Philco TP1454.
  (O TECC1040PG32T foi testado e perdeu canais de VHF.)
- Água entrando pelo cabo de antena no tuner já queimou o micro.

## Roteiro de diagnóstico sugerido

1. Inspeção visual: C318, C319, C310, C311, C634, C607 estufados? solda fria?
2. C607 descarregado! Depois medir +B em standby (~53 V) e ligado (114 V).
3. +B alto → R633, R617, R618, TL431, opto, R609. +B caindo → C634, C311, Q301, D302, C303, flyback, defletora.
4. +5 V no emissor de Q606 e +3V3 em Q602.
5. Com horizontal ativo: +180 V, ±16 V (D305, D306, R308, R309).
6. Só então suspeitar de IC301, EEPROM e, por último, IC201.
