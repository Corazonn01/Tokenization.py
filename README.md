# Tokenization.py
import nltk
from nltk.tokenize import word_tokenize
from nltk.stem import PorterStemmer, WordNetLemmatizer
from nltk.corpus import stopwords

# Download necessary NLTK data
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')

def preprocess_text(text):
    # Text normalization (lowercasing)
    text = text.lower()

    # Tokenization (splitting text into words)
    tokens = word_tokenize(text)
 
    # Removing stop words
    filtered_words = [word for word in tokens if word not in stopwords.words('english')]

    # Stemming and Lemmatization
    stemmer = PorterStemmer()
    lemmatizer = WordNetLemmatizer()
    stemmed_words = [stemmer.stem(word) for word in filtered_words]
    lemmatized_words = [lemmatizer.lemmatize(word) for word in filtered_words]

    return {
        "original_text": text,
        "filtered_words": filtered_words,
        "stemmed_words": stemmed_words,
        "lemmatized_words": lemmatized_words
    }
    
your_text = "Groundwater stands as a crucial and renewable resource globally, playing a vital role in the Earth's natural water cycle. This valuable resource, found in underground layers, primarily originates from sources such as rainwater and water flowing in streams. In the past, the methods employed to ascertain the existence and potential of groundwater involved various time-intensive and expensive techniques. These included drilling, alongside geophysical, geological, hydrogeological, and geo-electrical methods. However, these traditional approaches often fell short in terms of providing comprehensive coveragRecent advancements have highlighted that the integration of remote sensing and Geographic Information System (GIS) technologies presents a more efficient way to map and evaluate groundwater potential. This study explores the effectiveness of a GIS-based approach, utilizing the Modified DRASTIC Model. This model integrates various critical factors that have a direct impact on the presence and behavior of groundwater. It considers several surface attributes that are indicative of groundwater potential. These attributes encompass aspects such as the geological characteristics of the area, the texture of the soil, prevalent land use patterns, lithology, the typology of landforms, the degree of slope steepness, the presence and characteristics of lineaments, as well as the nature of the drainage systems in the region. In order to predict changes in groundwater potential, this study employed the MOLUSCE tool, a sophisticated plugin used in QGIS. This tool applies a combination of advanced techniques including Artificial Neural Networks (ANN), multicriteria evaluation, weights of evidence, and Logistic Regression (LRs) algorithms to predict changes in land use and land cover. The reliability of these predictions was notably high, as evidenced by a kappa value of 0.83. The analysis yielded insightful results, particularly concerning different regions' groundwater potential. For instance, it was observed that areas in the Southwest region consistently exhibited low to very low groundwater potential over the years. In contrast, the central region displayed a high to very high potential consistently. Moreover, the changes in potential over the years in these regions were minimal.However, a notable prediction made by the study is that by the year 2042, the eastern region of Kiambu County is expected to experience a decrease in groundwater potential. This insight is particularly important for future planning and management of water resources in the area. The application of these advanced GIS and remote sensing techniques, therefore, not only provides a more efficient and comprehensive method for assessing groundwater potential but also offers valuable foresight for effective water resource management."


# Preprocess the text
preprocessed = preprocess_text(your_text)

print("Original Text:", preprocessed['original_text'])
print("Filtered Words:", preprocessed['filtered_words'])
print("Stemmed Words:", preprocessed['stemmed_words'])
print("Lemmatized Words:", preprocessed['lemmatized_words'])
