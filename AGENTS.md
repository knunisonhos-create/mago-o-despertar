# AGENTS.md - MesaRPG

## Propósito
Aplicação web single-file para RPG de mesa (VTT leve) com:
- Autenticação (demo + preparado para Firebase)
- Ficha de personagem
- Anotações
- Regras/Dicas
- Mesa virtual colaborativa com drag & drop de tokens + limites de movimento

## Stack atual
- HTML + Tailwind via CDN + Font Awesome CDN
- JavaScript puro (sem build)
- localStorage para persistência local
- Estrutura preparada para Firebase (Auth + Firestore)

## Regras de movimento implementadas
- Clamp automático durante o drag baseado em `moveOriginX/Y` + `rangeSettings.moveSpeed`
- Círculos visuais: corpo a corpo (vermelho), curta distância (âmbar), movimento (verde tracejado)
- Reset de origem de movimento por token ou global

## Como editar
- Tudo está em `index.html` (um único arquivo grande mas organizado).
- Estado principal da mesa fica em `tokens[]` + `backgroundUrl`.
- Funções importantes: `startDrag`, `onMapPointerMove`, `onMapPointerUp`, `showRangesForSelected`, `addNewToken`.
- Persistência local: `persistLocalMapState()`.

## Futuro (Firebase)
- Substituir login demo por `firebase.auth()`
- Substituir `persistLocalMapState` + render por `onSnapshot` + `setDoc`
- Usar subcoleção `rooms/{roomId}/tokens/{tokenId}`
- Adicionar presença de jogadores (quem está online)

## Não fazer
- Não dividir em múltiplos arquivos JS/CSS a menos que migremos para Vite ou similar (o objetivo é deploy trivial no GitHub Pages).
- Manter o tema dark fantasy com acentos roxo/violeta.

## Testes manuais recomendados
1. Login demo → ir direto para Mesa
2. Arrastar tokens e verificar clamp de movimento
3. Selecionar token → mostrar alcances → resetar turno
4. Adicionar token novo + mudar fundo
5. Trocar de sala (room-id) e voltar (deve carregar estado separado)
6. Preencher ficha e salvar → recarregar a página
