# Typo Generation Project

This project generates synthetic typographical error datasets for six Indian languages: **Tamil**, **Kannada**, **Punjabi**, **Gujarati**, **Sanskrit**, and **Bengali**. It creates parallel data suitable for training spelling correction models or evaluating error‑tolerant NLP systems.

The dataset consists of word pairs in the format `input,target`:
- Correct word: both fields are identical.
- Typo: the first field contains a random typo, the second is the correct word.

## Why This Project Is Important

Typographical errors are ubiquitous in user‑generated content, search queries, and digitized texts. For many languages, especially those with rich morphology and non‑Latin scripts, there is a lack of publicly available datasets that model realistic spelling mistakes. This project addresses that gap by providing synthetic typo data for six Indian languages, enabling:

- **Training and evaluation of spelling correction models** – essential for search engines, messaging apps, and document editors.
- **Improving OCR post‑processing** – to correct errors introduced during optical character recognition of historical or printed texts.
- **Enhancing natural language understanding (NLU)** – making chatbots, virtual assistants, and machine translation systems more robust to noisy input.
- **Supporting low‑resource languages** – where real‑world error corpora are scarce, synthetic data serves as a practical alternative.
- **Research on error patterns** – by analysing the generated typos, one can study common error tendencies across scripts and languages.

By releasing these datasets and the generation script, we hope to lower the barrier for developing spelling‑aware applications for these languages and to foster further research in multilingual and cross‑script error modelling.

## Languages Covered
| Language   | Script       | File Name           |
|------------|--------------|---------------------|
| Tamil      | Tamil        | `tamil_typos.txt`   |
| Kannada    | Kannada      | `kannada_typos.txt` |
| Punjabi    | Gurmukhi     | `punjabi_typos.txt` |
| Gujarati   | Gujarati     | `gujarati_typos.txt`|
| Sanskrit   | Devanagari   | `sanskrit_typos.txt`|
| Bengali    | Bengali      | `bengali_typos.txt` |

Each file contains one correct line and one typo line per word (approximately 400–500 words per language).

## File Structure

typo_project/
├── generate_typos.py # Main script
├── tamil_typos.txt
├── kannada_typos.txt
├── punjabi_typos.txt
├── gujarati_typos.txt
├── sanskrit_typos.txt
├── bengali_typos.txt
└── README.md


## Requirements
- Python 3.6 or higher
- No external libraries (only uses `random` and `unicodedata` from the standard library)

## How to Run
1. Clone or download this repository.
2. Open a terminal in the project folder.
3. Run the script:
   ```bash
   python generate_typos.py

**Typo Generation Method**
For each word, one of four random operations is applied:

Insertion – a random character from the language’s character set is inserted at a random position.

Deletion – one character is removed.

Substitution – one character is replaced with another random character from the same set.

Swap – two adjacent characters are transposed.

The script ensures that the generated typo is different from the original word (up to three attempts). A fixed random seed (42) is used for reproducibility; you can change or remove it in the __main__ block to get different typos each run.

**Output Format**
Each line is a comma‑separated pair:

text
<possibly erroneous word>,<correct word>
Both fields are UTF‑8 encoded strings.

Example from tamil_typos.txt:

text
ஆறு,ஆறு
ஆறுப,ஆறு
நீர்,நீர்
நீர்ந,நீர்
...


**Data Source**
The word lists were extracted from an Excel file containing vocabulary sheets for each language. The original words cover a wide range of categories: nature, objects, abstracts, and common day‑to‑day terms.

**Customization / Adding New Languages**

To extend the project to another language:

Add a new word list (Python list of strings) in generate_typos.py.

Add the list to the language_words dictionary.

The script will automatically generate a file named <language>_typos.txt.