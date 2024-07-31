# Guess-the-word
python mini project



SOURCE CODE (no comments because small project)



#Made by big chilla
import random

words = "gamer", "python", "eggplant", "swapping", "keys", "phone"
secret_word = random.choice(words)
dashes = "-" * len(secret_word)


def get_guess():
    global dashes
    guesses_left = 10
    print(dashes)
    while True:
        attempt = input("Guess: ")
        if not attempt.islower():
            print("Your guess must be a lowercase letter!")
        elif len(attempt) > 1:
            print("Your guess must have exactly one character!")
        elif attempt in secret_word:
            dashes = update_dashes(secret_word, attempt, dashes)
            print("It's in the secret word!")
            print(dashes)
            if dashes == secret_word:
                print("Congratulations! You've guessed the word!")
                print(F"The secret word was {secret_word}")
                break
        elif guesses_left == 0:
            print("You are out of attempts. You have failed.")
            print(F"The secret word was {secret_word}")
            break
        else:
            guesses_left -= 1
            print(f"That is not in the secret word. You have {guesses_left} attempts left.")



def update_dashes(secret_word, attempt, dashes):
    result = ""
    for i in range(len(secret_word)):
        if secret_word[i] == attempt:
            result += attempt
        else:
            result += dashes[i]
    return result
    
    
get_guess()
