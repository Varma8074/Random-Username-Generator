# Random-Username-Generator

import random 
import string 
# Pre-defined lists of adjectives and nouns 
adjectives = ['Happy', 'Cool', 'Brave', 'Smart', 'Funky', 'Silly', 'Wild', 'Charming'] 
nouns = ['Tiger', 'Dragon', 'Phoenix', 'Knight', 'Pirate', 'Wizard', 'Lion'] 
 
def generate_username(include_number=True, include_special_char=True, length=8): 
    adjective = random.choice(adjectives) 
    noun = random.choice(nouns) 
    username = adjective + noun 
 
    if include_number: 
        username += str(random.randint(10, 99)) 
     
    if include_special_char: 
        username += random.choice(string.punctuation) 
 
    # Adjust length if necessary 
    return username[:length] if length < len(username) else username 
 
def save_usernames_to_file(usernames, filename='usernames.txt'): 
    with open(filename, 'w') as file: 
        for username in usernames: 
            file.write(username + '\n') 
    print(f'Usernames saved to {filename}') 
 
def main(): 
    print("Welcome to the Random Username Generator!") 
    num_usernames = int(input("How many usernames would you like to generate? ")) 
    include_number = input("Include numbers? (y/n): ").strip().lower() == 'y' 
    include_special_char = input("Include special characters? (y/n): ").strip().lower() == 'y' 
    length = int(input("Enter desired username length: ")) 
 
    usernames = [generate_username(include_number, include_special_char, length) for _ in 
range(num_usernames)] 
    print("\nGenerated Usernames:") 
    for username in usernames: 
        print(username) 
 
    save_usernames_to_file(usernames) 
 
if __name__ == '__main__': 
    main()
