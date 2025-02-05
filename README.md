# Random-Username-Generator

1. Objective 
The goal of this project is to create a Python program that generates unique and fun 
usernames suitable for social media or gaming platforms. This project helps practice 
fundamental Python concepts, including working with lists, randomization, and file 
handling. 
2. Project Features 
• - Generate usernames by combining random adjectives and nouns, such as 
'CoolTiger123' or 'HappyDragon!'. 
• - Allow customization options, including adding numbers or special characters and 
setting username length. 
• - Save generated usernames to a text file for future use or sharing. 
• - Provide interactive user input for specifying preferences, such as adding numbers or 
special characters. 
3. Implementation Details 
The project is divided into three main components: 
1. Random Username Generation: Combine adjectives and nouns randomly to generate 
unique usernames. 
2. User Preferences: Allow users to specify username length and whether to include 
numbers or special characters. 
3. File Handling: Save generated usernames to a text file. 
4. Python Source Code 
• Below is the complete Python code for the Random Username Generator:
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
