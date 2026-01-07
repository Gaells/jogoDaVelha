# 📸 Screenshots do Jogo da Velha

Esta pasta contém os screenshots do aplicativo para documentação.

## 🎯 Como Capturar os Screenshots

### Preparação
1. Execute o app no modo desenvolvimento: `npm start`
2. Abra no dispositivo/emulador de sua preferência
3. Configure para o idioma desejado (recomendado: Português ou Inglês)

### Screenshots Necessários

#### 1. `tela-inicial.png`
- **Descrição**: Tela inicial do jogo antes de qualquer jogada
- **Capturar**: 
  - Tabuleiro vazio (todas as células vazias)
  - Placar zerado (X: 0, O: 0, Empates: 0)
  - Botões de Nova Partida e Zerar Placares visíveis
  - Ícones de modo de jogo e idioma visíveis

#### 2. `jogo-em-andamento.png`
- **Descrição**: Jogo em andamento com algumas jogadas feitas
- **Capturar**:
  - 3-5 jogadas no tabuleiro (mix de X e O)
  - Indicador do turno atual visível
  - Nenhum vencedor ainda

#### 3. `vitoria.png`
- **Descrição**: Tela mostrando uma vitória
- **Capturar**:
  - Linha, coluna ou diagonal completa com X ou O
  - Modal de vitória exibido ("X venceu!" ou "O venceu!")
  - Células vencedoras destacadas (fundo verde)
  - Placar atualizado

#### 4. `seletor-idiomas.png`
- **Descrição**: Modal de seleção de idiomas aberto
- **Capturar**:
  - Tocar no ícone 🌐
  - Modal com lista de 8 idiomas visível
  - Bandeiras de cada país visíveis
  - Idioma atual marcado/destacado

#### 5. `configuracao-ia.png`
- **Descrição**: Modal de configuração do modo de jogo e IA
- **Capturar**:
  - Tocar no ícone de modo (👥 ou 🤖)
  - Opções "Jogador vs Jogador" e "Jogador vs IA"
  - Níveis de dificuldade (Fácil, Médio, Difícil)
  - Emojis e descrições visíveis

#### 6. `modo-pvp.png`
- **Descrição**: Jogo no modo Jogador vs Jogador
- **Capturar**:
  - Ícone 👥 visível no canto superior
  - Jogo em andamento no modo PvP
  - Interface limpa e clara

## 📐 Especificações Recomendadas

- **Formato**: PNG (melhor qualidade)
- **Resolução**: 
  - Mobile: 1080x2340 (ou resolução nativa do dispositivo)
  - Redimensionar para ~800px de largura para o README
- **Orientação**: Portrait (vertical)
- **Qualidade**: Alta (100%)

## 🛠️ Ferramentas para Captura

### Android
- Screenshot nativo: Power + Volume Down
- Android Studio: Camera icon no Device Manager
- ADB: `adb shell screencap -p /sdcard/screenshot.png`

### iOS
- iPhone X ou superior: Side Button + Volume Up
- iPhone 8 ou inferior: Home + Power
- Xcode: Cmd + S no Simulator

### Expo Go
- Shake device → Developer Menu → Take Screenshot

## 📝 Checklist

- [ ] `tela-inicial.png` - Tela inicial com tabuleiro vazio
- [ ] `jogo-em-andamento.png` - Jogo com algumas jogadas
- [ ] `vitoria.png` - Tela de vitória
- [ ] `seletor-idiomas.png` - Modal de idiomas
- [ ] `configuracao-ia.png` - Modal de configuração
- [ ] `modo-pvp.png` - Modo Jogador vs Jogador

## ✨ Dicas

1. Tire screenshots em um dispositivo real para melhor qualidade
2. Certifique-se de que não há informações sensíveis visíveis
3. Use o mesmo dispositivo/resolução para todos os screenshots (consistência)
4. Prefira fundos claros e interface limpa
5. Capture em horário com boa iluminação se for dispositivo físico
6. Considere tirar screenshots em múltiplos idiomas se necessário
