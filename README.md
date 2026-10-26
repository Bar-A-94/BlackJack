<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=180&section=header&text=BlackJack&fontSize=40&fontColor=ffffff&fontAlignY=36&animation=fadeIn&desc=Probability%20tables%20vs.%20Q-learning&descSize=15&descAlignY=58" width="100%" />

**Play Blackjack, then watch probability-based and RL players compete**

<img src="https://img.shields.io/badge/Python-30363d?style=for-the-badge&logo=python&logoColor=FFD43B" />
<img src="https://img.shields.io/badge/Q--Learning-30363d?style=for-the-badge" />
<img src="https://img.shields.io/badge/Probability-30363d?style=for-the-badge" />

</div>

<br/>

> [!NOTE]
> A full Blackjack engine plus six kinds of players, from a random player to Q-learning agents, compared over millions of training rounds.

## 🃏 The players

| | Player | How it decides |
|:-:|---|---|
| 🎲 | **Random** | Picks a random action |
| 🙋 | **Human** | You, through prompts |
| 📋 | **Basic strategy** | The standard basic strategy tables ([4 decks](https://wizardofodds.com/games/blackjack/strategy/4-decks/)) |
| 🧮 | **Expectancy** | My own strategy: a precomputed table of the expected value of each action, picking the best |
| 🤖 | **Q-learning (one step)** | Updates every action of a hand equally once it ends (lr 0.1) |
| 🤖 | **Q-learning (decay step)** | Updates with a decay of 0.9 over the actions of a hand (lr 0.1) |

Read more: [game rules](Game/) · [table players](Players/TablesPlayers/) · [RL players](Players/RLPlayers/)

## 📈 Results

<p align="center">
  <img src="compare/compare%201000%20games%20for%20each%20training%20session.png" width="80%" alt="Comparison of players across training sessions" />
</p>

**Lesson learned:** the Q-learning curves flatten out as training grows, and neither Q-learning player comes close to the basic strategy. Q-learning also learns to avoid risk, since losses weigh heavily on its decisions.

<details>
<summary><b>🔥 Decision tables (hard hands)</b></summary>

<br/>

| Basic strategy | Expectancy | Q-learning (one step) |
|:-:|:-:|:-:|
| <img src="Players/TablesPlayers/Heat%20map%20tables/Basic%20player%20Hard%20table.png" width="260" /> | <img src="Players/TablesPlayers/Heat%20map%20tables/Expectancy%20Hard%20table.png" width="260" /> | <img src="Players/RLPlayers/Heat%20map%20tables/QLearning1Step%20Hard%20table.png" width="260" /> |

</details>

## 🚀 Get started

```bash
git clone https://github.com/Bar-A-94/BlackJack.git
cd BlackJack
python main.py                 # play
python Train_and_compare.py    # train the RL players and compare
```

## 🗂️ Structure

```
BlackJack/
├── Game/                  # game engine and rules (one split per hand)
├── Players/
│   ├── RandomPlayer.py, HumanPlayer.py
│   ├── TablesPlayers/     # basic strategy + expectancy players
│   └── RLPlayers/         # Q-learning players + saved policies
├── Utility/Tables.py      # decision tables
├── compare/               # training and comparison logs
├── main.py                # play
└── Train_and_compare.py   # train and compare
```

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=100&section=footer" width="100%" />
