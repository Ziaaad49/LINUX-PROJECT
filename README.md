# LINUX-PROJECT
# guessinggame.sh

# Function to count the number of files in the current directory
function count_files {
    echo $(ls -1 | wc -l)
}

# Welcome message
echo "Welcome to the Guessing Game!"

# Store the correct number of files in a variable
correct_count=$(count_files)

# Loop until the user guesses correctly
while true; do
    # Prompt the user for a guess
    echo "How many files are in the current directory?"
    read guess

    # Validate input
    if ! [[ "$guess" =~ ^[0-9]+$ ]]; then
        echo "Please enter a valid number."
        continue
    fi

    # Check if the guess is correct
    if [[ $guess -lt $correct_count ]]; then
        echo "Too low, try again!"
    elif [[ $guess -gt $correct_count ]]; then
        echo "Too high, try again!"
    else
        echo "Congratulations! You guessed it right."
        break
    fi

done
