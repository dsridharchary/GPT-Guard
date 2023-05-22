# GPT-Guard Code Documentation
## Modules re and spacy
- python libraries re Module re standas for regular expression matching procedures are provided by this module.
- Python SpaCy is a Python library for natural language processing (NLP) tasks. It provides efficient pre-trained models for tasks like tokenization, part-of-speech tagging, named entity recognition, and dependency parsing. SpaCy is user-friendly, scalable, and supports multiple languages. It's widely used for various NLP applications in research and industry.
- This Python code utilizes the "re" and "spacy" libraries to extract and replace potentially sensitive data from a given text. The code provides functions to extract and replace text patterns such as IPv4 and IPv6 addresses, credentials, and custom strings. It also utilizes the spacy library to extract names and product entities from the text.

### setup python file(setup.py) 
python setup.py is a command used to interact with the setup.py file in a Python project. It allows you to perform actions such as building the project, installing it, creating distribution packages, running tests, and executing custom commands defined in the setup.py file.
## installation
- Create Virtual environment using this command to activate
```
 python3 -m venv envirinment-name or python -m venv envirinment-name and.
 ```
- to install 
```
 pip install gpt-guard or python3 setup.py install
```
- after that install spacy, run this command 
``` 
python -m spacy download en_core_web_sm
```
### requirements.txt
The requirements.txt file in Python is used to specify the external libraries or packages that a project depends on. It lists the required packages and their versions, and it is used with package management tools like pip to automatically install the dependencies. 
```
pip install requirements.txt
```
### GRP-gaurd/gpt_guard/__init__.py
The __init__.py file's primary function is to designate a directory as a Python package. An __init__.py file must be present in every directory containing code that you want to be able to import as a basic Python package. 
### GRP-gaurd/gpt_guard/extract_sensitive_data.py
This python file have Ten methods each method have specific task those are described in below
- extract(text, pattern): This function extracts every instance of a specified pattern from the supplied text using regular expressions.
- replace(text, words_to_replace, replacement) uses regular expressions to search the input text for particular words or patterns, and then replaces them with the replacement.
- extract_names(text, spacy_entities): This function applies natural language processing to the input text using the spacy library. Using the input data, it extracts entities categorised as "PERSON" or "PRODUCT" in order to find probable names. 
- extract_ipv4_addresses(text): Using regular expressions, the function extract_ipv4_addresses(text) extracts IPv4 addresses from the input text.
- extract_ipv6_addresses(text):Using regular expressions, the function extract_ipv6_addresses(text) extracts IPv6 addresses from the input text.
- find_credentials(text): This function searches the input text for potential credentials using regular expressions. It looks for words with at least eight characters in length, at least one letter, one digit, and one non-alphanumeric character.
- replace_with_placeholders(sentence, items, tag): This function replaces specific items in the input sentence with sequentially-numbered placeholders based on the provided tag. It returns the modified sentence and the list of replaced items.
- replace_custom_strings(sentence, custom_strings, tag): Based on the supplied tag, this function substitutes sequentially-numbered placeholders for user-defined strings in the input text. The updated sentence and a list of the custom strings that have been modified are returned.
- find_and_replace_sensitive_data(text, spacy_entities, custom_strings=[]): To identify and replace sensitive information in the input text, this function combines a number of extraction and replacement processes. Using the aforementioned functions, it collects names, IPv4 and IPv6 addresses, and possible credentials. Custom strings are also included if they are offered. The sanitised data is returned along with a list of changes that were done.
- sanitize_query(query, custom_identifiers=[], spacy_entities=["PERSON", "PRODUCT"], preamble="..."):By removing sensitive information from a query, this function sanitises it. The input query text is cleaned up using the find_and_replace_sensitive_data function. Additionally, a preamble is added to the sanitised input to let users know about the replacement placeholders. The cleaned-up query and a list of names for the deleted sensitive data will be provided.
### GRP-gaurd/gpt_guard/re_append_sensitive_data.py
Python file contains Two functions in the provided code interact to re-append sensitive data to a response. Below is a description of each function.
- replace_placeholders_with_items(sentence, items, tag): This function accepts three inputs: a sentence, a list of items, and a tag. The enumerate function, which provides both the index i and the associated item, is used to loop across the items. Based on the tag and index, it generates placeholders like "TAG_1", "TAG_2" and so on. The replace method is then used to swap out each instance of the placeholder with the corresponding item. The altered sentence is then returned.
- re_append_sensitive_data(gpt_output, removed_sanitized_data): The output of a response (gpt_output) and a list of deleted and sanitised data (removed_sanitized_data) are the two inputs for this function. It sets the value of gpt_output as the initial value of the variable result. The process then repeats over each tag and the list of objects it is connected with in removed_sanitized_data. It uses the replace_placeholders_with_items function for each tag and item list, passing the tag, the items, and the result. The sensitive data from the beginning is used to fill in the placeholders in the outcome. The corrected result is then returned.

