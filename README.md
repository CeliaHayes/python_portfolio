# python_portfolio_CeliaHayes
This is the portfolio of python code that I learned during BISC 450C.


## Python Fundamentals

 ```python
name = "Sara"
age = 22
height_cm = 164.3
print(f"{name} is {age} years old and {height_cm} cm tall.")
 ```
 ```python
dna = "ATCG"
print("DNA Length:", len(dna))
print("First base:", dna[0])
 ```


## Analyzing Data

 ```python
import pandas as pd
 ```
 ```python
data = pd.read_csv("example_data.csv")  # replace with your file
print(data.head())
 ```
 ```python
print("Average:", data["Value"].mean())
print("Min:", data["Value"].min())
 ```
 ```python
import matplotlib.pyplot as plt
 ```
 ```python
plt.plot(data["Value"])
plt.title("Values Over Time")
plt.xlabel("Index")
plt.ylabel("Value")
plt.show()
 ```

## Storing Values in List
 ```python
dna_bases = ["A", "T", "C", "G"]
print("First base:", dna_bases[0])
dna_bases.append("A")
print("Updated list:", dna_bases)
 ```


## Using Loops

 ```python
sequence = "ATGCGATAAGCT"
count_A = 0
 ```
 ```python
for base in sequence:
    if base == "A":
        count_A += 1
 ```
 ```python
print("Number of A's:", count_A)
 ```


## Using Multiple Files
 ```python
import glob
 ```
 ```python
files = glob.glob("data/*.txt")  # assumes .txt files in a folder called data/
 ```
 ```python
for filename in files:
    with open(filename, 'r') as f:
        contents = f.read()
        print(f"{filename}: {len(contents)} characters")
 ```


## Making Choices
 ```python
base = "A"
 ```
 ```python
if base == "A" or base == "T":
    print("It's a purine.")
elif base == "C" or base == "G":
    print("It's a pyrimidine.")
else:
    print("Not a valid DNA base.")
 ```


## Functions
 ```python
# Part 1 & 2
def add_bases(base1, base2):
    return base1 + base2
 ```
 ```python
# Part 3 & 4
def count_base(seq, target):
    count = 0
    for base in seq:
        if base == target:
            count += 1
    return count
 ```
 ```python
print(add_bases("A", "T"))
print("G count:", count_base("AGCTGGCTA", "G"))
 ```


## Defensive Programming
 ```python
def safe_divide(x, y):
    try:
  ```

        print("Error: Cannot divide by zero.")
        return None
  ```python
assert safe_divide(10, 2) == 5
assert safe_divide(5, 0) == None
 ```


## Transcribing DNA into RNA
 ```python
def transcribe_dna_to_rna(dna):
    return dna.replace("T", "U")
 ```
 ```python
dna = "ATGCGT"
rna = transcribe_dna_to_rna(dna)
print("RNA:", rna)
 ```


## Translating RNA into Protein
 ```python
codon_table = {
    "AUG": "M", "UUU": "F", "UUC": "F", "UAA": "*", "UAG": "*", "UGA": "*",
    # Add more codons for full translation
}
 ```
 ```python
def translate_rna(rna):
    protein = ""
    for i in range(0, len(rna)-2, 3):
        codon = rna[i:i+3]
        amino_acid = codon_table.get(codon, "?")
        protein += amino_acid
    return protein
 ```
 ```python
rna = "AUGUUUUAA"
protein = translate_rna(rna)
print("Protein:", protein)
 ```
