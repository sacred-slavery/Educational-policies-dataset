# To perform Critical Discourse Analysis (CDA) on documents, such as speeches, using Python, you can use Natural Language Processing (NLP) libraries. 

Steps to Build the Code:

1. Load the PDF Document: Use libraries like PyPDF2 or pdfplumber to extract text from PDF files.


2. Preprocess the Text: Clean the text by removing special characters, stopwords, and unnecessary whitespace.


3. Perform Semantic Analysis:

Moral and Ethical Content: Use predefined dictionaries (e.g., LIWC) or construct your own list of moral and ethical keywords.

Market-Oriented Language: Use a similar approach with a dictionary of market-related terms (e.g., "profit", "efficiency", "competition").

Treatment of Religion: Look for terms and phrases associated with religion or value-transcendent frameworks (e.g., "faith", "spiritual", "sacred").

Use sentiment analysis or other NLP techniques to understand how these concepts are treated (positively, negatively, or neutrally).



4. Measure the Degree of Presence: Count and normalize occurrences of these terms relative to the total word count.


5. Generate a Report: Visualize the results using plots or export them to a readable format (e.g., CSV or JSON).

### Explanation of Code:

1. Text Extraction: extract_text_from_pdf() reads the PDF file.


2. Text Cleaning: Removes unnecessary characters and stopwords.


3. Keyword Analysis: Counts occurrences of predefined keywords for each category.


4. Normalization: Converts counts into percentages relative to the total word count.


5. Visualization: Displays results in a bar chart for easy interpretation.

## how to preform preprocessing text 
To preprocess text for Critical Discourse Analysis (CDA), cleaning is a crucial step to ensure that your data is structured and ready for analysis. Below is a detailed explanation of how to clean text by removing special characters, stopwords, and unnecessary whitespace in Python.


---

Step-by-Step Preprocessing

1. Import Required Libraries

You’ll need the following Python libraries:

import re
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

# Download NLTK stopwords
nltk.download('stopwords')
nltk.download('punkt')


---

2. Define the Text Cleaning Function

Here’s a function that performs the preprocessing tasks:

def clean_text(text):
    # 1. Convert to lowercase
    text = text.lower()
    
    # 2. Remove special characters and numbers
    text = re.sub(r'[^a-z\s]', '', text)
    
    # 3. Tokenize the text into words
    words = word_tokenize(text)
    
    # 4. Remove stopwords
    stop_words = set(stopwords.words('english'))
    filtered_words = [word for word in words if word not in stop_words]
    
    # 5. Remove extra whitespaces (if joining back into a string)
    cleaned_text = ' '.join(filtered_words)
    
    return cleaned_text


---

3. Apply the Function

If you have a dataset or a document, you can apply this function to preprocess the text. Here’s an example:

# Example text
example_text = "The quick brown fox jumps over the lazy dog! This is a test, with numbers 123 and symbols #@$."

# Clean the text
cleaned_text = clean_text(example_text)
print(cleaned_text)

Output:

quick brown fox jumps lazy dog test numbers symbols


---

Explanation of Each Step

1. Convert to Lowercase:

Text normalization ensures case insensitivity during analysis.



2. Remove Special Characters and Numbers:

Using re.sub(r'[^a-z\s]', '', text) removes everything except lowercase letters and spaces.



3. Tokenize the Text:

Tokenization splits the text into individual words for more granular processing.



4. Remove Stopwords:

Stopwords (e.g., "and", "the", "is") are removed because they don’t contribute to the semantic meaning in most cases.

NLTK provides a predefined list of stopwords.



5. Remove Extra Whitespaces:

If you rejoin the tokens into a string, removing extra spaces ensures the cleaned text is well-formatted.





---

Additional Considerations

1. Language-Specific Stopwords:

If your text is not in English, specify the appropriate stopword list:

stop_words = set(stopwords.words('spanish'))  # For Spanish, for example



2. Retaining Important Words:

Customize your stopwords list if necessary to retain specific words important for CDA.



3. Handling Lemmatization/Stemming:

To reduce words to their base form, you can use:

from nltk.stem import WordNetLemmatizer
lemmatizer = WordNetLemmatizer()
lemmatized_words = [lemmatizer.lemmatize(word) for word in filtered_words]


Customization:

1. Expand the keyword lists for each category to better suit your needs.


2. Add phrase detection for more complex patterns (e.g., using nltk.collocations).


3. Use advanced NLP techniques, such as topic modeling (with gensim) or semantic similarity (with spaCy or transformers), for deeper insights.



### The CDA implementation is designed to analyze educational policy documents across three main dimensions:

1. Power Relations Analysis:
- Identifies patterns of authority and control in policy language
- Examines institutional power structures
- Detects spaces of resistance or agency

2. Market Discourse Analysis:
- Tracks frequency of market-oriented terminology
- Analyzes emphasis on efficiency and competition
- Examines neoliberal frameworks in education

3. Moral Discourse Analysis:
- Identifies value-based language
- Examines ethical frameworks
- Analyzes community and collective emphasis

### the CDA code processes documents:

This CDA implementation allows us to:
1. Systematically analyze power relations in educational policies
2. Identify and quantify market-oriented language
3. Examine moral and ethical frameworks
4. Generate comprehensive reports for comparative analysis

The code processes documents through:
1. Pattern Recognition: Identifies specific language patterns
2. Frequency Analysis: Measures occurrence of key terms
3. Contextual Analysis: Examines how terms are used
4. Structural Analysis: Analyzes document organization

## Application of Document Analysis in Our Study

def analyze_educational_systems():
    """
    Integrated analysis workflow for educational system comparison
    """
    # 1. Process Policy Documents
    documents = {
        'US': ['ESSA_2015.txt', 'State_Guidelines.txt', 'Character_Education.txt'],
        'Finland': ['Basic_Education_Act.txt', 'National_Core_Curriculum.txt'],
        'Chile': ['LGE_2009.txt', 'Curriculum_Framework.txt']
    }
    
    results = {}
    for country, docs in documents.items():
        country_results = {
            'market_metrics': [],
            'moral_metrics': [],
            'power_metrics': []
        }
        
        for doc in docs:
            # Apply CDA analysis
            cda_results = analyze_policy_document(doc)
            
            # Extract key metrics
            market_score = calculate_market_orientation(cda_results)
            moral_score = calculate_moral_framework(cda_results)
            power_score = calculate_power_relations(cda_results)
            
            # Store results
            country_results['market_metrics'].append(market_score)
            country_results['moral_metrics'].append(moral_score)
            country_results['power_metrics'].append(power_score)
        
        # Calculate aggregate scores
        results[country] = {
            'market_orientation': np.mean(country_results['market_metrics']),
            'moral_framework': np.mean(country_results['moral_metrics']),
            'power_relations': np.mean(country_results['power_metrics'])
        }
    
    return results

def calculate_sacred_slavery_index(country_results):
    """
    Calculate Sacred Slavery Index based on CDA results
    """
    weights = {
        'market_orientation': 0.4,
        'moral_framework': 0.3,
        'power_relations': 0.3
    }
    
    ssi_scores = {}
    for country, metrics in country_results.items():
        ssi = (
            weights['market_orientation'] * metrics['market_orientation'] +
            weights['moral_framework'] * (5 - metrics['moral_framework']) +  # Inverse relationship
            weights['power_relations'] * metrics['power_relations']
        )
        ssi_scores[country] = ssi
    
    return ssi_scores

def integrate_with_quantitative_data(cda_results, pisa_data, nces_data):
    """
    Integrate CDA findings with quantitative metrics
    """
    integrated_analysis = {}
    for country in cda_results.keys():
        # Combine CDA scores with quantitative metrics
        integrated_analysis[country] = {
            'ssi_score': calculate_sacred_slavery_index(cda_results)[country],
            'student_wellbeing': extract_wellbeing_metrics(pisa_data, country),
            'system_efficiency': calculate_system_efficiency(nces_data, country)
        }
    
    return integrated_analysis

### 

