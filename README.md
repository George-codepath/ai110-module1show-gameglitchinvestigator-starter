# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [X] Describe the game's purpose.
      The game’s purpose is to guess a hidden number before you run out of tries. The app is meant to tell you if your guess is too high, too low, or correct, while tracking your score.
- [X] Detail which bugs you found.
      1: New Game does not actually reset the game after a win/loss. 

      2: The displayed range and the actual new-game range do not respect difficulty. The UI always says Guess a number between 1 and 100

      3: Hint messages are inverted relative to the comparison result.

      4: Attempt counting is off by one and invalid input still consumes attempts


- [X] Explain what fixes you applied.
   1: New Game now fully reopens the game by setting status back to "playing". I also clear the guess history there, so the game starts fresh instead of staying stuck after a win or loss.

   2: The difficulty range is now used in both places it should be: the message now shows Guess a number between {low} and {high}, and New Game now creates the new secret number with random.randint(low, high) instead of always using 1 to 100
   

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
