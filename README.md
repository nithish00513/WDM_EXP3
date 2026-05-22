### EX3 Implementation of GSP Algorithm In Python
### AIM: To implement GSP Algorithm In Python.
### Description:
The Generalized Sequential Pattern (GSP) algorithm is a data mining technique used for discovering frequent patterns within a sequence database. It operates by identifying sequences that frequently occur together. GSP works by employing a depth-first search strategy to explore and extract frequent patterns efficiently.
### Steps:
1. <strong>Database Scanning:</strong> GSP scans the sequence database to determine the support of each item in the dataset.
2. <strong>Candidate Generation:</strong> It generates a set of candidate sequences using frequent items found in the previous step.
3. <strong>Pattern Growth:</strong> It extends the candidate sequences by merging them to form longer patterns, checking their support against a user-defined minimum support threshold.
4. <strong>Repeat:</strong> The process continues until no new sequences meet the minimum support threshold.
<p align="justify">
GSP finds application in various domains such as market basket analysis, web usage mining, bioinformatics, and more. For instance, in retail, GSP can identify common purchasing patterns, helping businesses understand customer behavior for targeted marketing or inventory management.
</p>

### Procedure:
<p align="justify">
1. From collections import defaultdict, from itertools import combinations: Imports necessary libraries/modules. defaultdict is
used to create a dictionary with default values and combinations generates all possible combinations of a sequence.</p>
<p align="justify">
2. generate_candidates(dataset, k): Function to generate candidate k-item sequences from a dataset. It loops through each sequence in the
dataset and finds combinations of length k for each sequence, updating their counts in a dictionary.</p>
<p align="justify">
3. gsp(dataset, min_support): Function that implements the Generalized Sequential Pattern (GSP) algorithm. It iterates through increasing
sequence lengths (k) until no new frequent patterns are found. It calls generate_candidates() to find patterns of varying lengths.</p>
<p align="justify">
4. Example dataset for each category: Defines example sequences for top wear, bottom wear, and party wear categories.</p>
<p align="justify">
5. Minimum support threshold: Sets the minimum support count required for a pattern to be considered frequent.</p>
<p align="justify">
6. Perform GSP algorithm for each category: Applies the GSP algorithm for each category using the defined example datasets and the
minimum support threshold.</p>
<p align="justify">
7. Output the frequent sequential patterns for each category: Prints the frequent sequential patterns 
    along with their support counts
for each wear category.</p>
<p align="justify">
8. Visulaize the sequence patterns using matplotlib.
</p>

### Program:

```python

from collections import defaultdict
from itertools import combinations

def generate_candidates(dataset, k, min_support):
    candidates = defaultdict(int)
    for seq in dataset:
        flat_seq = [item for itemset in seq for item in itemset]
        for comb in combinations(flat_seq, k):
            candidates[comb] += 1
    return {item: support for item, support in candidates.items() if support >= min_support}

def gsp(dataset, min_support):
    fp = defaultdict(int)
    k = 1
    while True:
        candidates = generate_candidates(dataset, k, min_support)
        if not candidates:
            break
        fp.update(candidates)
        k += 1
    return fp

dataset = [
    [["a","b","c"], ["b","e"], ["c","f","g"], ["a","b","e"]],
    [["a","d"], ["b","c"], ["c"], ["f","g"], ["c","h"]],
    [["b","c"], ["a","d"], ["e","b","f"], ["c","d","f","g","h"]],
    [["c"], ["e","c"], ["e","h"]]
]

dataset2 = [
    [["b","d"], ["c","b"], ["a","c"]],
    [["b","f"], ["c","e"], ["b"], ["f","g"]],
    [["a","h"], ["b","f"], ["a","b","f"]],
    [["b","e"], ["c","e"], ["d"]],
    [["a"], ["b","d"], ["b","c","b"], ["a","d","e"]]
]

min_support = 3

results = gsp(dataset, min_support)

print("Frequent Sequential Patterns for Dataset 1:")
if results:
    for pattern, support in results.items():
        print(f"Pattern: {pattern}, Support: {support}")
else:
    print("No frequent sequential patterns found.")



results = gsp(dataset2, min_support)

print("\nFrequent Sequential Patterns for Dataset 2:")
if results:
    for pattern, support in results.items():
        print(f"Pattern: {pattern}, Support: {support}")
else:
    print("No frequent sequential patterns found.")
```

       
### Output:

<img width="483" height="478" alt="image" src="https://github.com/user-attachments/assets/271cb6fa-eac0-427e-a08b-251abdd11614" />

<img width="414" height="484" alt="image" src="https://github.com/user-attachments/assets/532d0874-2d35-4fd9-a647-bd6f7be429e4" />

<img width="444" height="487" alt="image" src="https://github.com/user-attachments/assets/c101053f-22b6-40eb-b94f-e7933b4886be" />

<img width="481" height="493" alt="image" src="https://github.com/user-attachments/assets/d0d594e0-aa80-4cc1-a03f-1b862ebc02e3" />

<img width="459" height="484" alt="image" src="https://github.com/user-attachments/assets/468178d4-355a-4da9-8dd9-66d9fd0548d8" />

<img width="478" height="491" alt="Screenshot 2025-09-15 102009" src="https://github.com/user-attachments/assets/f0b117ec-126a-412b-a634-c12706ffb217" />

<img width="493" height="486" alt="image" src="https://github.com/user-attachments/assets/80b95b56-99ae-464a-97ec-e9341678cde0" />

<img width="526" height="489" alt="image" src="https://github.com/user-attachments/assets/b28bcd1a-d047-482d-98b4-a4cf854f10a2" />

<img width="645" height="492" alt="image" src="https://github.com/user-attachments/assets/c33b5471-f491-4697-b72f-a9872361868a" />

<img width="646" height="488" alt="image" src="https://github.com/user-attachments/assets/c322c1f7-cf23-4222-a86e-fb43e953eed2" />

<img width="464" height="489" alt="image" src="https://github.com/user-attachments/assets/8efb08c6-175d-4ed7-9a19-c25d4fd3c083" />

<img width="523" height="486" alt="image" src="https://github.com/user-attachments/assets/1539fe65-39eb-4262-a2c1-0637ff6e52cc" />

### Result:

Thus the implementation of the GSP algorithm in python has been successfully executed.
