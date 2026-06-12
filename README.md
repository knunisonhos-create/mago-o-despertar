# MesaRPG - Fichas & Tabuleiro Virtual em Tempo Real

Uma página web completa para RPG de mesa com:
- Login / Cadastro de jogadores
- Ficha de personagem editável
- Anotações pessoais
- Painel de Regras e Dicas
- **Mesa Virtual** (a parte mais importante): imagem de fundo + tokens arrastáveis com **sincronização em tempo real** quando configurado.

Todos os jogadores online veem os movimentos dos tokens ao vivo (drag & drop).

## Como usar agora (Modo Local / Demo)

1. Abra o arquivo `index.html` diretamente no navegador (duplo clique).
2. Use qualquer email e senha na tela de login (modo demo).
3. Vá direto para a aba **Mesa Virtual** (é a principal).
4. Arraste os tokens coloridos.
5. Clique em um token para selecionar → use os controles de alcance à direita.
6. Clique em "Adicionar Token" para criar novos.
7. **Criar nova cena**: o botão "+ Nova Cena (IA)" agora automaticamente gera e aplica um fundo temático feito por IA (imagens salvas na pasta `backgrounds/`). A imagem já aparece preenchendo o quadro amarelo corretamente.
8. **Substituir fundo**: o botão "Substituir Fundo" troca a imagem da cena atual que você selecionou. Após escolher o arquivo, a imagem é exibida dentro do quadro amarelo e o app oferece baixar o arquivo para você copiar manualmente para a pasta `backgrounds/` se quiser mantê-lo como asset do projeto.

**Funciona 100% offline/localmente** usando localStorage. Perfeito para testar sozinho ou em rede local (compartilhando o arquivo).

**Limitação atual**: Em modo demo, cada pessoa tem sua própria visão. Para verem juntos em tempo real, configure o Firebase (abaixo).

## Deploy no GitHub Pages (Recomendado)

### Opção mais fácil e gratuita:

1. Crie um repositório novo no GitHub (público ou privado).
2. Faça upload do arquivo `index.html` (e deste README).
3. Vá em **Settings → Pages**.
4. Em "Source", escolha "Deploy from a branch" → Branch: `main` / Folder: `/ (root)`.
5. Salve. Aguarde ~1 minuto.
6. Sua página estará em: `https://SEU_USUARIO.github.io/NOME_DO_REPO`

Pronto! Qualquer um com o link consegue acessar.

**Google Sites não é recomendado** para isso — não suporta JavaScript interativo avançado nem drag-and-drop em tempo real.

## Como ativar MULTIPLAYER REAL (Firebase) — JÁ IMPLEMENTADO

O código já tem integração completa com Firebase!

### Passos exatos:

1. Acesse https://console.firebase.google.com e crie um projeto novo (ex: `mesarpg-seu-nome`).

2. Dentro do projeto:
   - **Authentication** → Sign-in method → Ative **Email/Password**
   - **Firestore Database** → **Create database** → escolha "Start in test mode" (depois você pode apertar as regras).

3. No menu lateral, clique no ícone `</>` ("Web") para registrar um app web.
   - Dê um apelido (ex: MesaRPG Web)
   - Copie o objeto inteiro `firebaseConfig`.

4. Abra o arquivo `index.html` e procure por:
   ```js
   window.FIREBASE_CONFIG = {
     apiKey: "SUA_API_KEY_AQUI",
     ...
   };
   ```
   Substitua pelos valores reais do seu projeto.

5. Salve o arquivo.

6. Recarregue a página (ou re-abra no GitHub Pages).

Pronto! Agora:
- Cadastro e login são reais (contas salvas no Firebase).
- Qualquer pessoa que abrir a mesma "sala" (campo "sessao-principal" ou outro nome) verá os tokens se movendo em tempo real.
- Fundo da mesa também é sincronizado.
- Cada sala é independente (mude o texto do campo "room-id" e clique "Entrar na Sala").

### Regras do Firestore (importante!)

Depois de testar, vá em **Firestore Database → Rules** e cole algo assim (mais seguro):

```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /rooms/{roomId} {
      allow read, write: if request.auth != null;
    }
    match /rooms/{roomId}/tokens/{tokenId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

Publique as regras.

O sistema já cuida de:
- Login/registro real
- Sincronização de posição de tokens (drag)
- Criação/remoção de tokens
- Background da cena
- Múltiplas salas (room-id)

## Regras de Movimento Implementadas

Na aba **Mesa Virtual** (barra lateral direita):

- **Velocidade por turno** (px): limite de arrasto a partir do ponto de origem do turno.
- **Corpo a corpo** (px): círculo vermelho.
- **Curta distância** (px): círculo âmbar.

**Como usar as regras**:
- Ao arrastar um token, ele **não passa** do limite de movimento (clamp automático).
- Botão **"Resetar Turno"** (no token selecionado) ou **"Resetar todos os turnos"** define o novo ponto de origem do movimento.
- Botão **"Mostrar alcances do token"** desenha os círculos de corpo a corpo + curta distância + movimento.

Dica: Defina a velocidade na ficha do personagem (campo "Velocidade (px/turno)") e use o mesmo valor na mesa.

## Atalhos de Teclado

- `/` → Abre o modal de adicionar token (quando na Mesa)
- `R` → Reseta o turno do token selecionado
- `Esc` → Fecha modais / deseleciona

## Próximos Passos (sugestões)

- [ ] Integração completa com Firebase (auth real + Firestore realtime)
- [ ] Upload de imagens de fundo e tokens (Firebase Storage)
- [ ] Chat da mesa
- [ ] Controle de "dono" do token (só o dono ou GM move)
- [ ] Modo Mestre com visão de todos os tokens escondidos
- [ ] Grade com escala real (ex: 1 quadrado = 5 pés)
- [ ] Salvamento automático da ficha no Firebase por usuário
- [ ] Múltiplas cenas/salas com lista

## Dica de imagens de fundo e tokens

Use sites como:
- https://www.reddit.com/r/battlemaps/
- https://2minutetabletop.com/
- https://inkarnate.com/
- Ou gere com IA e hospede no Imgur, Discord, ou GitHub (raw).

Tokens ficam ótimos com cores sólidas + iniciais. Para arte, use imagens pequenas com fundo transparente.

## Testando localmente

- Duplo clique no `index.html` (funciona na maioria dos navegadores).
- Ou rode um servidor simples:
  - PowerShell: `cd mesa-rpg ; python -m http.server 8080`
  - Depois acesse http://localhost:8080

## Próximos passos que posso implementar

- Upload real de imagens (Firebase Storage)
- Chat ao vivo na mesa
- Sistema de "dono do token" (só o dono ou o mestre move)
- Modo "Mestre" com fog of war / visão
- Histórico de ações / log de turnos
- Ficha mais completa com rolagem de dados integrada

É só pedir!

---

Projeto feito para ser simples de hospedar (GitHub Pages) e poderoso o suficiente para grupos pequenos jogarem de verdade.