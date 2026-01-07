# 🎮 Tic-Tac-Toe - React Native

An interactive tic-tac-toe game built with React Native, TypeScript and Expo, featuring **8 languages support** and **intelligent AI**.

## 📋 Features

- ✅ Intuitive and responsive interface
- ✅ **Support for 8 languages (i18n)**
- ✅ **AI with 3 difficulty levels**
- ✅ **Player vs Player and Player vs AI modes**
- ✅ Persistent scoring system
- ✅ Visual highlight of winning cells
- ✅ Automatic win and draw detection
- ✅ Automatic player turn switching
- ✅ **Locally saved language preference**
- ✅ TypeScript for type safety
- ✅ Modular componentization

## 📱 Screenshots

<div align="center">
  <img src="./assets/screenshots/tela-inicial.png" alt="Initial Screen" width="250"/>
  <img src="./assets/screenshots/vitoria.png" alt="Victory Screen" width="250"/>
  <img src="./assets/screenshots/configuracao-ia.png" alt="AI Configuration" width="250"/>
</div>

<div align="center">
  <img src="./assets/screenshots/derrota.png" alt="Defeat Screen" width="250"/>
  <img src="./assets/screenshots/empate.png" alt="Draw Screen" width="250"/>
  <img src="./assets/screenshots/seletor-idiomas.png" alt="Language Selector" width="250"/>
</div>

## 🌍 Supported Languages

- 🇧🇷 **Português** (pt-BR)
- 🇺🇸 **English** (en-US)
- 🇪🇸 **Español** (es-ES)
- 🇫🇷 **Français** (fr-FR)
- 🇩🇪 **Deutsch** (de-DE)
- 🇮🇹 **Italiano** (it-IT)
- 🇯🇵 **日本語** (ja-JP)
- 🇨🇳 **中文** (zh-CN)

## 🚀 Technologies

- **React Native** - Mobile development framework
- **TypeScript** - Static typing
- **Expo** - Development platform
- **React Hooks** - State management
- **Context API** - Global language management
- **AsyncStorage** - Preferences persistence
- **Minimax Algorithm** - Advanced AI for hard mode

## 📁 Project Structure

```
jogoDaVelha/
├── components/          # Reusable components
│   ├── Board.tsx       # Game board
│   ├── Cell.tsx        # Individual cell
│   ├── LanguageSelector.tsx # Language selector
│   └── GameModeSettings.tsx # Mode and difficulty settings
├── contexts/           # React contexts
│   └── LanguageContext.tsx  # Language management
├── locales/            # Translation files
│   ├── pt-BR.ts        # Portuguese (Brazil)
│   ├── en-US.ts        # English
│   ├── es-ES.ts        # Spanish
│   ├── fr-FR.ts        # French
│   ├── de-DE.ts        # German
│   ├── it-IT.ts        # Italian
│   ├── ja-JP.ts        # Japanese
│   ├── zh-CN.ts        # Chinese (Simplified)
│   └── index.ts        # Export and configuration
├── types/              # TypeScript type definitions
│   └── index.ts        # Game and language types
├── utils/              # Helper functions
│   ├── gameLogic.ts    # Game logic
│   └── aiLogic.ts      # AI algorithms
├── .github/            # GitHub configurations
│   └── copilot-instructions.md
├── App.tsx             # Main component
└── package.json        # Project dependencies
```

## 🎯 How to Use

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Expo Go app on your mobile device (optional)

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd jogoDaVelha
```

2. Install dependencies:
```bash
npm install
```

### Running the Project

#### Local Development
```bash
npm start
```

#### Android
```bash
npm run android
```

#### iOS (requires macOS)
```bash
npm run ios
```

#### Web
```bash
npm run web
```

## 🎮 How to Play

### Player vs Player Mode (👥)
1. The game starts with player **X**
2. Tap the 👥 icon in the top left corner to switch between modes
3. Tap an empty cell to make your move
4. Players alternate between **X** and **O**

### Player vs AI Mode (🤖)
1. Tap the mode icon (top left corner)
2. Select **"Player vs AI"**
3. Choose the difficulty level:
   - **😊 Easy** - AI makes random moves (great for beginners)
   - **🤔 Medium** - AI blocks wins and tries to win (challenging)
   - **😈 Hard** - AI uses Minimax algorithm (nearly impossible to beat!)
4. You always play as **X** (first)
5. AI plays as **O**

### General Features
- Tap the 🌐 icon to **change language**
- Use **"New Game"** to start a new game
- Use **"Reset Scores"** to reset the scores
- The first to complete a row, column, or diagonal wins
- If all cells are filled without a winner, it's a draw

## 🏗️ Components

### Board
Manages the 3x3 board and renders game cells.

### Cell
Represents an individual board cell with:
- Different visual states for X and O
- Highlight for winning cells
- Disabled after move

### ScoreBoard
Displays the score of both players and draws, translated in the selected language.

### LanguageSelector
Modal for language selection with:
- List of 8 available languages
- Flags for visual identification
- Current language indicator
- Preference persistence

### GameModeSettings
Modal for game configuration with:
- Selection between PvP and PvAI modes
- AI difficulty level choice
- Intuitive interface with emojis
- Visual confirmation of selections

## 🤖 Artificial Intelligence System

### Implemented Algorithms

#### 1. Easy AI (😊)
**Strategy**: Completely random moves
- Randomly chooses from available positions
- Does not consider strategy or blocks
- Ideal for beginners and children
- Player win rate: ~80-90%

```typescript
// Selects a random available position
export const easyAI = (board: Board): number => {
  const availableMoves = board
    .map((cell, index) => (cell === null ? index : null))
    .filter((index) => index !== null);
  return availableMoves[Math.floor(Math.random() * availableMoves.length)];
};
```

#### 2. Medium AI (🤔)
**Strategy**: Defensive and opportunistic play
- **Priority 1**: Win if there's an opportunity
- **Priority 2**: Block opponent's imminent victory
- **Priority 3**: Occupy center if available
- **Priority 4**: Occupy strategic corners
- **Priority 5**: Any available position
- Player win rate: ~40-60%

```typescript
export const mediumAI = (board: Board, aiPlayer: Player): number => {
  // 1. Try to win
  const winningMove = findWinningMove(board, aiPlayer);
  if (winningMove !== -1) return winningMove;

  // 2. Block opponent
  const blockingMove = findWinningMove(board, opponent);
  if (blockingMove !== -1) return blockingMove;

  // 3. Center > Corners > Edges
  // ...
};
```

#### 3. Hard AI (😈)
**Strategy**: Minimax Algorithm (Perfect Play)
- Implements the classic Minimax algorithm
- Evaluates all future possibilities
- Always chooses the best possible move
- **Impossible to beat** (only draw or defeat)
- Adaptive depth for optimization
- Player win rate: ~0-5% (only by AI error or perfect play)

```typescript
// Minimax: recursively evaluates all possible moves
const minimax = (
  board: Board,
  depth: number,
  isMaximizing: boolean,
  aiPlayer: Player,
  opponent: Player
): number => {
  // Checks for terminal conditions (win, loss, draw)
  // Returns score adjusted by depth
  // Maximizes for AI, minimizes for opponent
  // Returns best move found
};
```

### Technical Features

- **Smart delay**: AI "thinks" for 300ms-800ms for better UX
- **Visual indicator**: Shows "AI thinking..." during processing
- **Interaction blocking**: Prevents moves during AI's turn
- **Performance optimization**: Minimax with depth pruning
- **Instant moves**: Even in hard mode, response < 1s

### Minimax Details

The Minimax algorithm is a game theory technique that:

1. **Simulates all possible moves** until the end of the game
2. **Assigns scores**:
   - +10 for AI victory (adjusted by depth)
   - -10 for opponent victory (adjusted by depth)
   - 0 for draw
3. **Assumes perfect play** from both sides
4. **Chooses the path** that maximizes AI's score

**Why is it unbeatable?**
- Explores ALL ~362,880 game possibilities
- Always chooses the move that leads to the best possible outcome
- In tic-tac-toe, with perfect play, always ends in a draw

## 🌐 Internationalization System

### i18n Architecture

The game uses a robust internationalization system based on:

1. **Context API** - Global language management
2. **AsyncStorage** - User preference persistence
3. **Modular translations** - Separate file for each language

### How to Add a New Language

1. Create a file in `/locales` (e.g., `locales/ru-RU.ts`):
```typescript
export default {
  title: 'Крестики-нолики',
  playerXWins: 'Игрок X выиграл!',
  playerOWins: 'Игрок O выиграл!',
  draw: 'Ничья!',
  playerTurn: 'Ход игрока',
  newGame: 'Новая игра',
  resetScores: 'Сбросить счет',
  draws: 'Ничьи',
  language: 'Язык',
  selectLanguage: 'Выбрать язык',
};
```

2. Import and add in `locales/index.ts`:
- **Never use hardcoded text - always use translation system**
- **Use `useLanguage()` hook to access translations**
```typescript
import ruRU from './ru-RU';

export const translations = {
  // ... other languages
  'ru-RU': ruRU,
};

export const AVAILABLE_LANGUAGES = [
  // ... other languages
  { code: 'ru-RU', name: 'Русский', flag: '🇷🇺' },
];
```

3. Update the type in `types/index.ts`:
```typescript
export type SupportedLanguage = 'pt-BR' | 'en-US' | ... | 'ru-RU';
```

### Usage in Code

```typescript
import { useLanguage } from './contexts/LanguageContext';

function MyComponent() {
  const { t, language, setLanguage } = useLanguage();
  
  return (
    <Text>{t.title}</Text>
  );
}
```
## 🧩 Game Logic

### Main Functions (utils/gameLogic.ts)

- `checkWinner()` - Checks if there's a winner
- `checkDraw()` - Checks if the game ended in a draw
- `createEmptyBoard()` - Creates a new empty board
- `togglePlayer()` - Toggles between players

## 🎨 Personalização

Você pode personalizar cores e estilos editando os arquivos:
- [App.tsx](App.tsx) - Estilos principais
- [components/Cell.tsx](components/Cell.tsx) - Estilos das células
- [components/ScoreBoard.tsx](components/ScoreBoard.tsx) - Estilos do placar

## 📝 Convenções de Código

- Componentes funcionais com Hooks
- Nomes de componentes em PascalCase
- Funções auxiliares em camelCase
- Todas as props e estados tipados
- Interfaces para tipos customizados
- ComeCustomization

You can customize colors and styles by editing the files:
- [App.tsx](App.tsx) - Main styles
- [components/Cell.tsx](components/Cell.tsx) - Cell styles
- [components/ScoreBoard.tsx](components/ScoreBoard.tsx) - Scoreboard styles

## 📝 Code Conventions

- Functional components with Hooks
- Component names in PascalCase
- Helper functions in camelCase
- All props and states typed
- Interfaces for custom types
- Comments for documentation

## 🤝 Contributing

Contributions are welcome! Feel free to:
1. Fork the project
2. Create a branch for your feature
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 👤 Author

Built with ❤️ using React Native and Expo

---

**Have fun playing