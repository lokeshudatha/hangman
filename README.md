# hangman
import random
import hangman_stages

word = ["loki", "lokesh", "uda"]
chosen_word = random.choice(word)
print(chosen_word)
lives = 6
empty = []
for i in range(len(chosen_word)):
    empty += "_"
print(empty)
game_over = False
while not game_over:
    guessed = input("guess your letter: ").lower()
    for position in range(len(chosen_word)):
        letter = chosen_word[position]
        if letter == guessed:
            empty[position] = guessed
    print(empty)
    if guessed not in chosen_word:
        lives -= 1
        if lives == 0:
            game_over = True
            print("you lose")
    if "_" not in empty:
        game_over = True
        print("you win")
    print(hangman_stages.stages[lives])

