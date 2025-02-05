# Username-generator
import random

# Extended lists of adjectives and nouns
adjectives = ["Cool", "Happy", "Wild", "Mighty", "Silent", "Fast", "Adventurous", "Bold", "Brave", 
              "Clever", "Curious", "Fierce", "Friendly", "Glorious", "Graceful", "Joyful", "Legendary", 
              "Lightning", "Lucky", "Noble", "Radiant", "Reckless", "Royal", "Strong", "Swift", "Supreme", 
              "Tenacious", "Unstoppable", "Valiant", "Vibrant", "Wicked", "Wise", "Zany", "Mysterious", "Zealous"]

nouns = ["Tiger", "Dragon", "Lion", "Bear", "Eagle", "Shark", "Panther", "Unicorn", "Phoenix", "Wolf", 
         "Falcon", "Cobra", "Rhino", "Leopard", "Wolf", "Kraken", "Cyclone", "Volcano", "Comet", "Falcon", 
         "Ninja", "Samurai", "Wizard", "Pirate", "Captain", "Knight", "Emperor", "Gladiator", "Rebel", "Spy", 
         "Avenger", "Warrior", "Titan", "Dragonfly", "Kraken", "Ghost"]

# Function to generate a random username with underscore between parts
def generate_username(add_numbers=False, add_special_chars=False):
    # Combine a random adjective and noun with underscore
    username = random.choice(adjectives) + "_" + random.choice(nouns)
    
    # Optionally add numbers with an underscore between them
    if add_numbers:
        username += "_" + str(random.randint(1, 100))  # Random number between 1 and 100
    
    # Optionally add special characters with an underscore
    if add_special_chars:
        special_chars = ["@", "#", "$", "%", "&"]
        username += "_" + random.choice(special_chars)
    
    return username

# Function to save the generated usernames to a file
def save_to_file(usernames, filename="usernames.txt"):
    with open(filename, "a") as file:  # Open file in append mode
        for username in usernames:
            file.write(username + "\n")  # Write each username on a new line

# Function to handle user input for customization options
def get_user_input():
    # Ask the user whether to include numbers or special characters
    add_numbers = input("Do you want to add numbers? (y/n): ").strip().lower() == "y"
    add_special_chars = input("Do you want to add special characters? (y/n): ").strip().lower() == "y"
    
    return add_numbers, add_special_chars

# Main function that ties everything together
def main():
    print("Welcome to the Random Username Generator!")
    
    # Get customization options from the user
    add_numbers, add_special_chars = get_user_input()

    # Ask how many usernames the user wants to generate
    num_usernames = int(input("How many usernames would you like to generate? "))
    
    # Generate the specified number of usernames
    usernames = [generate_username(add_numbers, add_special_chars) for _ in range(num_usernames)]

    # Display the generated usernames
    print("\nGenerated Usernames:")
    for username in usernames:
        print(username)
    
    # Save the generated usernames to a file
    save_to_file(usernames)
    print("\nUsernames have been saved to 'usernames.txt'.")

# Run the program
if __name__ == "__main__":
    main()
