# Define a function to count word occurrences in a text file
def count_word_occurrences(file_name):
    # Create an empty dictionary to store word counts
    word_counts = {}

    try:
        # Open the file for reading
        with open(file_name, 'r') as file:
            # Iterate through each line in the file
            for line in file:
                # Split the line into words
                words = line.split()
                # Iterate through each word
                for word in words:
                    # Remove punctuation and convert to lowercase
                    cleaned_word = word.strip('.,!?()[]{}"\'').lower()
                    # Update word counts in the dictionary
                    if cleaned_word:
                        if cleaned_word in word_counts:
                            word_counts[cleaned_word] += 1
                        else:
                            word_counts[cleaned_word] = 1
    
        # Print unique words and their counts
        for word, count in word_counts.items():
            print(f'{word}: {count}')
    
    except FileNotFoundError:
        print(f"File '{file_name}' not found.")

# Call the function with the filename of your text file
file_name = '/content/kezpython.txt'
count_word_occurrences(file_name)
