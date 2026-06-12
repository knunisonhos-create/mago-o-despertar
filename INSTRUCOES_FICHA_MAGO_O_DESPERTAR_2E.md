# Instruções Completas para Criar Ficha Digital Preenchível
## Mago: O Despertar – 2ª Edição (Fiel à Imagem Fornecida)

Este documento contém uma descrição **extremamente detalhada** da ficha oficial de Mago: O Despertar 2ª Edição, baseada nas imagens JPG/PDF fornecidas pelo usuário. O objetivo é permitir que qualquer IA ou desenvolvedor reproduza **o layout visual mais fiel possível** em HTML + CSS + JS (ou qualquer outra tecnologia).

---

## 1. Estilo Visual Geral (Muito Importante)

- **Tema**: Gótico / Arcano / Pergaminho antigo
- **Fundo da ficha**: Tom creme/amarelado envelhecido (ex: `#f5f0e1` ou `#f8f1e3`), com textura sutil de papel (pode usar `background-image` com ruído ou `repeating-linear-gradient` muito suave)
- **Bordas**: Ornamentadas, com cantos decorativos (use `border` com imagens ou CSS `border-image`, ou divs com pseudo-elementos para cantos góticos)
- **Títulos**: Fontes serifadas elegantes (ex: `Georgia`, `Playfair Display`, `Cinzel`, ou `UnifrakturCook` para títulos grandes)
- **Cor do texto principal**: Marrom escuro / preto suave (`#3f2a1f` ou `#2c2118`)
- **Círculos de traços**:
  - Vazios: `○` (stroke apenas, cor escura)
  - Preenchidos: `●` (fill da mesma cor)
  - Ou use `<circle>` em SVG ou divs com `border-radius: 50%` + `border` + `background`
- **Quadrados** (Saúde, Força de Vontade): Pequenos quadrados brancos com borda, que ficam "preenchidos" (cor escura ou com X) quando marcados
- **Alinhamento**: Muito rigoroso em colunas e grids. A ficha tem forte simetria e hierarquia visual clara.

---

## 2. Estrutura Geral da Página (Layout)

A ficha é dividida em **duas grandes áreas verticais**:

### PARTE SUPERIOR (aprox. 55-60% da altura)
- Cabeçalho com título + dois selos místicos
- Seção IDENTIFICAÇÃO (linha de campos)
- Bloco grande dividido em 3 partes principais lado a lado:
  1. **Atributos** (coluna esquerda estreita)
  2. **Perícias** (centro, dividido em 3 subcolunas: Mental / Física / Social)
  3. **Direita**: Méritos (esquerda dessa área) + Especializações (direita dessa área)

### PARTE INFERIOR (aprox. 40-45% da altura)
- Linha horizontal dos **10 Arcanos** (símbolos grandes + 5 círculos abaixo de cada um)
- Abaixo dos Arcanos, um grid de 3 colunas principais:
  - **Esquerda**: TRAÇOS SOBRENATURAIS (Gnose + Sabedoria)
  - **Centro**: SAÚDE (10 quadrados) + FORÇA DE VONTADE (10 quadrados)
  - **Direita**: MANA (10 círculos) + caixas pequenas (Defesa, Velocidade, Iniciativa, Tamanho)
- Linha inferior com caixas:
  - **NIMBUS** (grande, linhas)
  - **FERRAMENTA DEDICADA** (linhas)
  - **ASPIRAÇÕES** (3 campos: Curto Prazo 1, Curto Prazo 2, Longo Prazo)
  - **OBSESSÕES** (área larga de texto)
  - **EXPERIÊNCIA** (canto inferior direito, com beats e XP)

---

## 3. Descrição Campo por Campo (Parte Superior)

### 3.1 Cabeçalho Principal

```
[MAGIC SEAL - 5 pointed star in circle]          [SWORD / STAFF vertical through ornate circle with runes]

MAGO
— O DESPERTAR —
2ª EDIÇÃO

IDENTIFICAÇÃO   (título menor centralizado ou à esquerda)
```

**Campos de Identificação** (em linhas com rótulo à esquerda + linha para preencher à direita):

- Nome:
- Nome Sombrio:
- Jogador:
- Crônica:
- Conceito:
- Virtude:
- Vício:
- Caminho:
- Ordem:
- Legado:
- Idade:
- Nacionalidade:

**Dica de implementação**: Use uma grid de 2 ou 3 colunas. Cada campo = `<label>` + `<input type="text" class="ficha-line">`. A "linha" pode ser simulada com `border-bottom` no input quando vazio.

### 3.2 Bloco de Atributos (Coluna Esquerda)

Título: **ATRIBUTOS**

Dividido em 3 subgrupos com fundo ou borda separando:

**MENTAIS**
- Inteligência      ●○○○○   (5 círculos)
- Raciocínio        ●○○○○
- Determinação      ●○○○○

**FÍSICOS**
- Força             ●○○○○
- Destreza          ●○○○○
- Vigor             ●○○○○

**SOCIAIS**
- Presença          ●○○○○
- Manipulação       ●○○○○
- Autocontrole      ●○○○○

**Implementação recomendada**:
- Cada atributo: label + container de 5 círculos clicáveis
- Círculos devem ser pequenos (14-18px)
- Clique alterna entre vazio e preenchido (ou define o valor exato clicando no n-ésimo círculo)

### 3.3 Bloco de Perícias (Centro + Direita)

Título: **PERÍCIAS**

Dividido em **3 colunas verticais**:

**MENTAIS**
- Acadêmicos ○○○○○
- Computador ○○○○○
- Ofícios ○○○○○
- Investigação ○○○○○
- Medicina ○○○○○
- Ocultismo ○○○○○
- Política ○○○○○
- Ciência ○○○○○

**FÍSICAS**
- Atletismo ○○○○○
- Briga ○○○○○
- Direção ○○○○○
- Armas de Fogo ○○○○○
- Furto ○○○○○
- Furtividade ○○○○○
- Sobrevivência ○○○○○
- Armas Brancas ○○○○○

**SOCIAIS**
- Lider com Animais ○○○○○
- Empatia ○○○○○
- Expressão ○○○○○
- Intimidação ○○○○○
- Persuasão ○○○○○
- Socialização ○○○○○
- Manha ○○○○○
- Subterfúgio ○○○○○

**Observação**: Os círculos de perícias começam **vazios** (diferente de atributos que geralmente têm 1 preenchido).

### 3.4 Méritos + Especializações (Abaixo dos Atributos / ao lado das Perícias)

**MÉRITOS** (caixa com borda)
- 10 linhas numeradas (1. a 10.)
- Cada linha: espaço para nome do Mérito + círculos de nível (geralmente 1 a 5)

**ESPECIALIZAÇÕES (Passivas)** (caixa ao lado)
- Título: ESPECIALIZAÇÕES (Pasivas)
- Várias linhas em branco para escrever (ex: "Investigação (Cenas de Crime)", "Ocultismo (Espíritos)")

---

## 4. Descrição Campo por Campo (Parte Inferior)

### 4.1 Os 10 Arcanos (Linha mais importante visualmente)

Cada Arcano tem:
- Um **símbolo circular grande** no topo (desenhar ou usar SVG)
- Nome do Arcano abaixo do símbolo (em maiúsculo, fonte forte)
- **5 círculos** embaixo para o nível (○○○○○)

Lista exata + sugestão de símbolo:

1. **MORTE** — caveira ou foice
2. **DESTINO** — roda da fortuna / estrela de 8 pontas / símbolo de teia
3. **FORÇAS** — raio / relâmpago
4. **VIDA** — folha / árvore / símbolo de vida
5. **MATÉRIA** — cubo / hexágono / engrenagem
6. **MENTE** — olho aberto com pupila
7. **PRIME** — estrela flamejante / sol com raios
8. **ESPAÇO** — círculo com setas saindo em 4 direções ou portal
9. **ESPÍRITO** — chama / fogo místico / espiral
10. **TEMPO** — ampulheta ou relógio antigo

**Dica técnica**: Crie um array de objetos no JS:
```js
const arcanos = [
  { id: 'death', name: 'MORTE', symbol: '💀' }, // ou SVG
  ...
]
```

### 4.2 Traços Sobrenaturais (Esquerda)

**TRAÇOS SOBRENATURAIS**

- **GNOSE** — 10 círculos (geralmente divididos visualmente em dois grupos de 5)
- **SABEDORIA** — 10 círculos

### 4.3 Saúde + Força de Vontade (Centro)

**SAÚDE**
- 8 a 10 quadradinhos em linha (brancos com borda)
- Normalmente:  Vigor + Tamanho (padrão 7-9)

**FORÇA DE VONTADE**
- 10 quadradinhos abaixo ou ao lado

### 4.4 Mana + Atributos Derivados (Direita)

**MANA**
- 10 círculos (pode ter uma linha de "Mana Atual" e "Mana Máxima")

Abaixo:
- DEFESA
- VELOCIDADE
- INICIATIVA
- TAMANHO

Cada um com uma caixinha pequena para número.

### 4.5 Caixas Inferiores

- **NIMBUS** (grande, lado esquerdo) — título + várias linhas para descrição
- **FERRAMENTA DEDICADA** — título + linhas
- **ASPIRAÇÕES**
  - Curto Prazo 1: ________
  - Curto Prazo 2: ________
  - Longo Prazo: ________
- **OBSESSÕES** — caixa larga com várias linhas
- **EXPERIÊNCIA** (canto inferior direito)
  - BEATS NORMAIS □□□□□
  - BEATS ARCANO □□□□
  - EXP. NORMAL □□□□□
  - EXP. ARCANA □□□□
  - Símbolo de XP (geralmente um círculo com "XP" ou estrela)

---

## 5. Recomendações Técnicas de Implementação (HTML + CSS + JS)

1. **Container principal**
   - `max-width: 800px` ou `900px`
   - `margin: 0 auto`
   - `background: #f5f0e1`
   - `box-shadow: 0 10px 30px rgba(0,0,0,0.3)`
   - Borda ornamentada (pode usar `border: 8px solid #3f2a1f` + cantos com pseudo-elements)

2. **Círculos / Dots Component**
   - Crie um componente reutilizável (função JS que gera 5 divs)
   - Cada círculo deve ter `data-value`
   - Ao clicar no 3º círculo, preenche os 3 primeiros
   - Armazene o valor no objeto do personagem

3. **Quadrados de Saúde / Vontade**
   - Use `display: inline-flex` com quadrados de 14px
   - Clique marca com `background-color` ou desenha um X via CSS

4. **Inputs de linha**
   - Estilo `border: none; border-bottom: 1px solid #3f2a1f; background: transparent;`

5. **Símbolos dos Arcanos**
   - Melhor opção: SVGs inline (crie 10 SVGs simples)
   - Alternativa boa: Unicode + cores + tamanho grande + label abaixo

6. **Responsividade**
   - A ficha oficial não é responsiva. Em web, considere:
     - Versão desktop fiel (800-900px)
     - Versão mobile com "compact mode" (ou aviso "melhor visualizada em tela larga")

---

## 6. Estrutura de Dados Sugerida (JavaScript)

```js
const character = {
  // Identificação
  name: "", shadowName: "", player: "", chronicle: "", concept: "",
  virtue: "", vice: "", path: "", order: "", legacy: "", age: "", nationality: "",

  // Atributos
  attributes: { intelligence: 1, wits: 1, resolve: 1, ... },

  // Perícias (todas 0-5)
  skills: { academics: 0, ... },

  // Méritos e Especializações
  merits: [{name: "", dots: 2}, ...],
  specializations: [],

  // Arcana
  arcana: { death: 0, fate: 0, ... },

  // Traços
  gnosis: 1,
  wisdom: 7,

  // Pools
  health: { max: 8, damage: [] },   // array de estados
  willpower: { max: 5, used: 0 },
  mana: { current: 10, max: 10 },

  defense: 2, speed: 5, initiative: 4, size: 5,

  nimbus: "",
  dedicatedTool: "",
  aspirations: { short1: "", short2: "", long: "" },
  obsessions: "",

  beats: { normal: 0, arcane: 0 },
  experience: { normal: 0, arcane: 0 }
}
```

---

## 7. Próximos Passos Recomendados

1. Criar um CSS dedicado (`.mage-sheet`, `.arcane-symbol`, `.dot`, `.health-box`)
2. Fazer o header com dois SVGs dos selos
3. Implementar o grid exato da parte superior primeiro (Atributos + Perícias + Méritos)
4. Depois implementar a linha dos 10 Arcanos (é a parte mais icônica)
5. Por último as caixas inferiores
6. Integrar com o sistema atual de roles (Jogador vs Mestre)

---

**Documento gerado para uso com IA ou desenvolvedor.**  
Use este arquivo como prompt principal ao pedir para outra IA gerar o HTML/CSS da ficha.

Se quiser, posso agora implementar uma versão **muito mais fiel** no `index.html` usando essas instruções.