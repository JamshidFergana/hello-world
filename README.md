# hello-Assalomu-Aleykum

Bismillahir Rohmanir Rohim.

'''
import random

WORDS = ['Ar-Rohman', 'Ar-Rohim', 'Al-Molik']

max_errors = 10

def return_random_word():
    return random.choice(WORDS)

def user_handle_input():
    user_input = input('Please input a letter: ')
    if user_input not in 'abcdefghijklmnopqistuvwxyz':
        print('Please input a string!')
        return user_input

def get_initial_statuses(word):
    statuses = []
    for letter in word:
        statuses.append(False)
    return statuses    

def is_game_finished(statuses, current_error):
    if current_error >= max_errors:
        return True
    
    for status in statuses:
        if not status:
            return False
            
    return True        

def perform_check_action(word, statuses, letter):
    if letter not in word:
        return False
    
    for index, l in enumerate(word):
        if letter == l:
            statuses[index] = True
            
    return True        

def print_word(word, statuses):
    for index, letter in enumerate(word):
        if statuses[index]:
            print(letter, end="")
        else:
            print('_', end=" ")
    print()        

def main():
    word = return_random_word()
    statuses = get_initial_statuses(word)
    current_error = 0 
    
    while not is_game_finished(statuses, current_error):
        print_word(word, statuses)
        print('Erros left: ', max_errors - current_error)
        letter = user_handle_input()
        result = perform_check_action(word, statuses, letter)
        
        if not result:
            current_error += 1 
    if current_error >= max_errors:
        print('You lose!')
    else:
        print('You win!')
    
main()
