# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

The first time I ran the game, it looked normal at first, but after playing I noticed several bugs. One big problem was that the hint logic was wrong. For example, when the secret number was higher than my guess, the game sometimes told me to go lower instead of higher. Another bug was that after winning and clicking New Game, the app did not reset correctly for the next round. The “you already won” message stayed on the screen, and the developer debug history also did not fully reset after starting a new game.

---

## 2. How did you use AI as a teammate?

I used GitHub Copilot in VS Code and ChatGPT on this project. I used Copilot to look at the code, explain possible bugs, suggest fixes, help move code from `app.py` to `logic_utils.py`, and help make a pytest test. I used ChatGPT to help me understand the instructions and to check whether the AI suggestions made sense.

One AI suggestion that was correct was about the hint bug. The AI suggested that the comparison logic should stay simple and that the secret number should stay a number, not change type. I checked this by running the Streamlit app again and testing guesses that were higher, lower, and equal to the secret number. I also ran pytest, and the test passed.

One AI suggestion that was misleading was an early code suggestion for the hint fix. It was not fully correct the first time, so I did not accept it right away. I checked the diff, read the code carefully, and tested the game again until the hints worked correctly and all tests passed.

---

## 3. Debugging and testing your fixes

I decided a bug was really fixed by testing the same problem again after I changed the code. If the game worked correctly in the same case that was broken before, then I knew the fix was probably correct. I also checked the code changes to make sure they made sense.

One test I ran was a pytest test in `tests/test_game_logic.py` for the hint bug. It checked three cases: a guess higher than the secret, a guess lower than the secret, and a correct guess. All the tests passed, and this showed me that `check_guess()` was now giving the correct result and message. I also tested the New Game button by hand and saw that the old win message disappeared and the history reset.

AI helped me understand and create the test. Copilot suggested a pytest test that directly checked the bug I fixed. This helped me test the code in a clear and repeatable way.

---

## 4. What did you learn about Streamlit and state?

I learned that Streamlit reruns the whole script when the user clicks a button or changes an input. Because of that, the app needs a way to remember important values between reruns. That is why `session_state` is important.

If I explain it simply, Streamlit reruns are like rebuilding the app again and again after every action. `session_state` is the memory of the app. It stores things like the secret number, attempts, score, status, and history. If the state is not reset correctly, old values and messages can stay on the screen and cause bugs.

---

## 5. Looking ahead: your developer habits

One habit I want to use again in future projects is testing the same bug case again after making a fix. This helped me know if the code really worked. I also want to keep asking AI about one bug at a time and then carefully checking the diff.

Next time I work with AI on a coding task, I will be more careful before accepting the first suggestion. I learned that AI can help a lot, but I still need to read the code, test it, and make sure it is really correct.

This project changed the way I think about AI-generated code. Now I see that AI is a helpful teammate, but I should not trust it blindly. It can help me work faster, but I still need to verify the final result myself.