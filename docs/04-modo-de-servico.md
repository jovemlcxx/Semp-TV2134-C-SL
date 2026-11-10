# 4. Modo de serviço, modo desenvolvimento e ajustes

Fonte principal: manual de serviço MSTV(3)-071 do TV2134(B)SL (chassi SK11). Confirmado em vídeo por técnicos
no (B)SL e no (C)SL (ver `videos/`).

> **Antes de mexer: anote ou fotografe TODOS os valores de todas as páginas.** Não existe "restaurar padrão".
> A EEPROM guarda ajustes únicos do seu tubo.

## Entrar no modo de serviço (páginas 0 a 3)

1. Pressione **MENU** no controle remoto (o menu aparece na tela).
2. Em seguida, rapidamente, pressione **1** e depois **9**. Aparece a página 0.
3. Troque de página com **MENU** (páginas 0 e 1) ou com as teclas **0, 1, 2, 3**.
4. **CH+ / CH-** seleciona o item; **VOL+ / VOL-** altera o valor.
5. Para sair: tecla **"S"** do controle (nos vídeos, o "xis"/sair do controle). Não precisa desligar.

É preciso o controle original CT-7260 ou um compatível "completo" (com teclas numéricas e MENU).

## Entrar no modo desenvolvimento (páginas 0 a 15)

1. Já no modo de serviço, tecle **0** (página 0).
2. Com **CH+**, selecione o item **VLIN** (o manual grafa "VELIN").
3. Tecle **8** e depois **9**.
4. Aparece a página "0" do modo desenvolvimento; **MENU** percorre as páginas 0 a 15.

O modo desenvolvimento contém as opções de configuração do UOC (bits de opção, sistemas, entradas, etc.).
O manual não documenta essas páginas. Há um vídeo percorrendo **todos os parâmetros no 2134(C)**:
`videos/` → "Como Entrar No Modo De Serviço Da Tv Semp 2134(C), TODOS OS PARÂMETROS Do Modo Desenvolvimento".
**Alterar itens aqui sem saber pode deixar a TV sem imagem.**

## Tabela de dados de referência da EEPROM (IC202): TV2134(B)SL

Valores "típicos" do manual. O valor correto do seu aparelho é o que estava gravado nele.

| Página 0: geometria | Dado | Página 1: geometria | Dado | Página 2: escala de cinza | Dado | Página 3 | 21" | 29" |
|---|---|---|---|---|---|---|---|---|
| HPOS (posição H) | 34 | DPC (pincushion) | 52 | BLC | 7 | AGC | 24 | 24 |
| WID (largura) | 54 | KEY (trapézio) | 31 | RC (cutoff R) | 27 | SUB-BRI | 10 | 10 |
| VCEN (centro V) | 28 | CNRT (cantos sup.) | 56 | BC (cutoff B) | 32 | VLINE | 25 | 40 |
| VPOS (posição V) | 37 | CNRB (cantos inf.) | 53 | GC (cutoff G) | 38 | | | |
| HIT (altura) | 39 | HPAR (paralelogramo) | 30 | RD (drive R) | 31 | | | |
| VLIN (linearidade V) | 34 | HBOW (arco) | 29 | GD (drive G) | 30 | | | |
| | | | | BD (drive B) | 30 | | | |

> O tubo slim do 21" usa correção E/W (pino 16 do UOC → circuito EW). Se DPC/KEY/CNRT/CNRB não surtem efeito,
> o defeito é de hardware no circuito EW, há vídeo sobre "correção no circuito EW" do 2134(B)SL e relatos de
> "efeito taça/almofada" (ver [05](05-defeitos-e-solucoes.md)).

## Procedimentos do manual

### Escala de cinza (TV2134: sem AKB)
1. Sinal branco (gerador ou canal).
2. Página 3 → **VLINE**: o vertical fecha (linha horizontal). Gire o **SCREEN** no flyback até a linha
   (verde, vermelha ou azul) ficar **levemente visível**.
3. Página 2: ajuste **RC, BC, GC** (parte escura). A cor que apareceu primeiro no passo 2 é a referência, não mexa nela;
   ajuste as outras duas até o branco.
4. Ajuste **GD e BD** para que os brancos intensos fiquem sem predominância de cor.

(No 2934, com AKB: página 3 → VLINE → girar o SCREEN até aparecer "OK"; "HIGH"/"LOW" = reprovado.)

### Sub-brilho
Contraste no mínimo, brilho e cor no centro → página 3 → **SUB-BRI** até as áreas escuras não ficarem "afogadas"
e as claras não desfocarem. Conferir com brilho/contraste no máximo e no mínimo.

### Foco
Potenciômetro FOCUS no flyback T302, com um canal sintonizado.

### Geometria
HPOS → WID → VCEN (centro coincidindo com a barra escura) → VPOS → HIT → VLIN (metade superior = inferior) →
DPC → KEY → CNRT/CNRB → HPAR → HBOW.

## Troca de EEPROM

- O manual diz que IC202 só deve ser trocada por uma **gravada pela Semp**; com memória virgem a TV liga, mas desajustada.
- Os dados do 2134 e do 2934 **são diferentes**.
- Na prática (fóruns): técnicos colocam 24C08 virgem para testar se o defeito é "de software"; a TV liga e os valores
  são refeitos pelo modo de serviço usando a tabela acima como ponto de partida.
- **Faça backup da sua EEPROM enquanto a TV funciona** (gravador CH341A + clipe SOIC/DIP, 24C08). É a única cópia
  dos ajustes do seu tubo. Guarde o `.bin` em `eeprom/` neste repositório.
- Não foi encontrado dump público confiável do 2134(B)/(C)SL. Os dumps que circulam (4shared) são do **(A)SL: chassi SL11**,
  que usa outro micro e **não servem**.

## Outros métodos Semp Toshiba (NÃO são do SK11: só para referência)

- Chassi com micro Toshiba (ex.: 2134(A)SL / SL11, linha U): **MUTE** → de novo **MUTE** segurando + **MENU** no painel
  (ou VOL+ e VOL- juntos) → aparece "S" no canto. CH± seleciona, VOL± ajusta; desligar para sair.
- Guia genérico de TVs chinesas com TDA12165PS (firmware de outro fabricante): MENU + 6-4-8-3. **Não confirmado no SK11**
  (o firmware da Semp usa MENU-1-9). Texto em `fontes/foruns/electronicshelponline-service-mode-TDA12165.txt`.
