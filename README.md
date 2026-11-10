# Semp Toshiba TV2134(C)SL — biblioteca técnica (chassi SK11)

Base de conhecimento sobre a TV de tubo slim de 21" **Semp Toshiba TV2134(C)SL** e sua família (chassi **SK11**;
29" = **SK91**): manuais, esquema, pinagens, modo de serviço, defeitos resolvidos por técnicos, peças alternativas,
possibilidades de mod e transcrições de vídeos.

> ⚠️ TV de tubo tem alta tensão letal mesmo desligada. Leia [docs/08-seguranca.md](docs/08-seguranca.md) antes de abrir.

## Resumo em 30 segundos

- **CI principal:** TDA12165PS (NXP UOC‑TOP, micro + processador de vídeo num só) · **EEPROM:** 24C08
- **Fonte:** STR‑W6554A · **+B = 114 V** · **Vertical:** LA78040/LA78141/UTC78045 (±16 V) · **Saída H:** 2SD2553
- **Áudio:** TDA8944 (2×5 W) + TDA9850 (BTSC) · **Flyback:** BSC25‑N1587
- **Entradas:** RF, AV composto, **componente YPbPr** (15 kHz), saída AV
- **Modo de serviço:** `MENU` → `1` → `9` · **Modo desenvolvimento:** dentro dele, em VLIN, `8` → `9`
- **Senha do bloqueio de canais:** `1984`
- **Pontos fracos:** Q606 (regulador 5 V), C634/C311, R633, D305/D306, C318/C319, C613, solda fria

## Índice

| Documento | Conteúdo |
|---|---|
| [01 – Identificação e especificações](docs/01-identificacao-e-especificacoes.md) | Variantes (A)/(B)/(C), ficha técnica, conexões, recursos, limitações |
| [02 – Arquitetura e CIs](docs/02-arquitetura-e-cis.md) | Mapa de semicondutores, **pinagem completa do TDA12165PS com tensões**, vertical, flyback |
| [03 – Fonte de alimentação](docs/03-fonte-de-alimentacao.md) | Primário, secundário, tensões do STR, malha do +B, standby |
| [04 – Modo de serviço](docs/04-modo-de-servico.md) | Entrada, tabela de dados da EEPROM, procedimentos de ajuste, troca de memória |
| [05 – Defeitos e soluções](docs/05-defeitos-e-solucoes.md) | ~80 casos resolvidos organizados por sintoma |
| [06 – Peças e equivalências](docs/06-pecas-e-equivalencias.md) | Substitutos, kit de recap, compatibilidade entre modelos |
| [07 – Mods e possibilidades](docs/07-mods-e-possibilidades.md) | Componente/RGB, retro games, melhorias de confiabilidade, limites |
| [08 – Segurança](docs/08-seguranca.md) | Alta tensão, primário quente, descarga |
| [09 – Fontes e links](docs/09-fontes-e-links.md) | De onde veio cada coisa, **o que falta baixar manualmente**, lacunas |
| [Minha unidade](docs/minha-unidade.md) | Ficha para anotar os dados do seu aparelho |

## Estrutura

```
manuais/      manual de serviço (PDF + texto), manual do usuário, lista de peças
esquemas/     esquema SK11 e SK91 em PNG 300 dpi + recortes por bloco
datasheets/   datasheets dos CIs
docs/         conhecimento organizado (comece por aqui)
fontes/       texto bruto de fóruns e bases de dicas
videos/       índice de 39 vídeos + transcrições
eeprom/       (vazio) lugar para o backup da sua 24C08
```

## Avisos sobre a qualidade da informação

- O manual de serviço e o esquema aqui são do **TV2134(B)SL**. O (C)SL usa o mesmo chassi SK11 e os relatos de reparo citam
  as mesmas posições de componentes, mas o manual específico do (C) ainda precisa ser baixado à mão
  (ver [09](docs/09-fontes-e-links.md)). Confira sempre a serigrafia da sua placa.
- Dicas de fórum e vídeo são relatos de terceiros, não testados aqui.
- Transcrições de vídeo são legendas automáticas e têm muitos erros.
- O **TV2134(A)SL é outro chassi (SL11)** — esquemas, EEPROM e modo de serviço dele não servem.
