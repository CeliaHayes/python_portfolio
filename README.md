# python_portfolio
This is the portfolio of python code that I learned during BISC 450C.


## Python Fundamentals


name = "Alice"
age = 25
height_cm = 165.4
print(f"{name} is {age} years old and {height_cm} cm tall.")

dna = "ATCG"
print("DNA Length:", len(dna))
print("First base:", dna[0])



## Analyzing Data


import pandas as pd

data = pd.read_csv("example_data.csv")  # replace with your file
print(data.head())


print("Average:", data["Value"].mean())
print("Min:", data["Value"].min())


import matplotlib.pyplot as plt

plt.plot(data["Value"])
plt.title("Values Over Time")
plt.xlabel("Index")
plt.ylabel("Value")
plt.show()


## Storing Values in List

dna_bases = ["A", "T", "C", "G"]
print("First base:", dna_bases[0])
dna_bases.append("A")
print("Updated list:", dna_bases)



## Using Loops


sequence = "ATGCGATAAGCT"
count_A = 0

for base in sequence:
    if base == "A":
        count_A += 1

print("Number of A's:", count_A)



## Using Multiple Files

import glob

files = glob.glob("data/*.txt")  # assumes .txt files in a folder called data/

for filename in files:
    with open(filename, 'r') as f:
        contents = f.read()
        print(f"{filename}: {len(contents)} characters")



## Making Choices

base = "A"

if base == "A" or base == "T":
    print("It's a purine.")
elif base == "C" or base == "G":
    print("It's a pyrimidine.")
else:
    print("Not a valid DNA base.")



## Functions

# Part 1 & 2
def add_bases(base1, base2):
    return base1 + base2

# Part 3 & 4
def count_base(seq, target):
    count = 0
    for base in seq:
        if base == target:
            count += 1
    return count


print(add_bases("A", "T"))
print("G count:", count_base("AGCTGGCTA", "G"))



## Defensive Programming

def safe_divide(x, y):
    try:
        return x / y
    except ZeroDivisionError:
        print("Error: Cannot divide by zero.")
        return None

assert safe_divide(10, 2) == 5
assert safe_divide(5, 0) == None



## Transcribing DNA into RNA

def transcribe_dna_to_rna(dna):
    return dna.replace("T", "U")

dna = "ATGCGT"
rna = transcribe_dna_to_rna(dna)
print("RNA:", rna)



## Translating RNA into Protein

codon_table = {
    "AUG": "M", "UUU": "F", "UUC": "F", "UAA": "*", "UAG": "*", "UGA": "*",
    # Add more codons for full translation
}

def translate_rna(rna):
    protein = ""
    for i in range(0, len(rna)-2, 3):
        codon = rna[i:i+3]
        amino_acid = codon_table.get(codon, "?")
        protein += amino_acid
    return protein

rna = "AUGUUUUAA"
protein = translate_rna(rna)
print("Protein:", protein)
