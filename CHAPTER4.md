#  **RESULTS AND DISCUSSION**

This chapter presents a comprehensive analysis of the research findings
in relation to the three primary objectives: identifying employment
trends through data preprocessing, evaluating employment opportunities
using the Random Forest algorithm, and developing a predictive web
application. The discussions are supported by empirical evidence derived
from model performance metrics, feature importance analysis, and user
experience evaluation.

## **Employment Trends and Skill Demands Through Data Preprocessing**

To effectively identify employment trends and evolving skill demands,
detailed data preprocessing steps were undertaken to ensure the
consistency and quality of the professional profiles dataset. The
research utilized the Professional Profiles dataset from Hugging Face, a
comprehensive collection comprising 76,294 profiles. Each profile
initially contained four primary data columns: education level, skills,
experience, and current job role. An initial exploratory analysis of
this raw data revealed a diverse landscape with 639 unique job roles and
34 distinct skills distributed across the dataset.

A comprehensive preprocessing pipeline was subsequently implemented to
transform this raw data into structured features suitable for machine
learning analysis. The \'education level\' data underwent ordinal
encoding to accurately capture the hierarchical nature of academic
qualifications, with values assigned from 1 (High School) to 6
(Professional Degree). This method preserved the inherent progression of
educational attainment while converting categorical information into a
numerical format. The \'skills\' column, originally consisting of
comma-separated text values, was transformed into a set of binary
features, where \'1\' indicated the presence and \'0\' the absence of
each unique skill identified in the dataset. This vectorization approach
enabled the model to learn the importance of specific skills. For the
\'experience\' field, which contained unstructured text descriptions,
several meaningful numerical features were extracted using text analysis
techniques; these included total years of experience, a binary indicator
for any prior experience, and the count of previous jobs mentioned.
Finally, the target variable, \'current job role,\' was subjected to
label encoding, transforming the 639 unique textual values into numeric
indices essential for model training, while a mapping file was
maintained to ensure the interpretability of the results.

### **Dataset Characteristics and Composition.** The study utilized the Professional Profiles dataset from Hugging Face, which provided a robust foundation for the analysis. 

### Education Distribution. **T**his dataset contained 76,294 profiles with four primary data columns: education level, skills, experience, and current job role. Initial exploratory analysis revealed 639 unique job roles and 34 distinct skills across the dataset. Analysis of education levels revealed that Bachelor\'s degrees were the most common (35.6%), followed by High School (23.7%) and Associate\'s degrees (18.7%). Advanced degrees like PhD were relatively rare (0.3%)

![A graph of a number of people AI-generated content may be
incorrect.](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image5.png){width="4.255208880139983in"
height="2.8399507874015746in"}

Experience Distribution. The distribution of professional experience
demonstrated a right-skewed pattern, with the majority of individuals
possessing between 0-10 years of experience. The calculated mean
experience was 6.3 years with a standard deviation of 6.7 years,
indicating considerable variability in professional tenure across the
dataset. Analysis showed that 80.2% of entries had some experience, with
an average of 1.3 previous jobs per individual.![A graph of a
distribution of years AI-generated content may be
incorrect.](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image6.png){width="4.401042213473316in"
height="2.9234733158355204in"}

Skill distribution. In terms of skills distribution, problem-solving
(43.4%), time management (43.2%), and communication (43.2%) emerged as
the three most prevalent skills in the dataset. The most common skills
in the dataset were problem-solving, time management, and communication,
each present in over 40% of the resumes. Technical skills like machine
learning, programming, and data analysis were present in approximately
15-16% of resumes.![A graph of skills distribution AI-generated content
may be
incorrect.](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image3.png){width="4.197916666666667in"
height="2.985411198600175in"}

Job Role Distribution. The dataset contained 639 unique job roles, with
a relatively balanced distribution. The most common roles included
Marine scientist, technical author, and Pathologist, each representing
less than 0.2% of the dataset![A graph with text and numbers
AI-generated content may be
incorrect.](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image1.png){width="3.901042213473316in"
height="2.7878412073490813in"}

Education vs. Job Role. Analysis revealed strong relationships between
education levels and job roles. For example, Professional Degrees were
strongly associated with healthcare roles like Pathologist and Child
psychotherapist, while PhDs were more common in research and academic
positions.![A graph of different colored squares AI-generated content
may be
incorrect.](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image2.png){width="4.867924321959755in"
height="3.245087489063867in"}

Experience vs. Job Role. Years of experience varied significantly across
job roles. Senior positions like Chief Financial Officer showed higher
average years of experience, while entry-level positions had lower
levels.

![A graph with blue squares AI-generated content may be
incorrect.](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image8.png){width="3.7343755468066493in"
height="2.6645800524934384in"}

Skills vs. Job Role. The heatmap analysis of skills across job roles
revealed distinct skill patterns for different career paths. Technical
roles showed higher prevalence of programming and data analysis skills,
while management positions had higher rates of leadership and strategic
planning skills.

### **Data Preprocessing and Feature Engineering.** A comprehensive preprocessing pipeline was implemented to transform the raw dataset into structured features suitable for machine learning analysis. The education data underwent ordinal encoding to capture the hierarchical nature of academic qualifications, with values ranging from 1 (High School) to 6 (Professional Degree). This approach preserved the inherent progression of educational attainment while converting categorical information into numerical values for model training.

The skills column, originally containing comma-separated text values,
was transformed into a set of binary features representing the presence
(1) or absence (0) of each unique skill identified in the dataset. This
vectorization approach allowed the model to learn the importance of
specific skills for different job roles while maintaining a consistent
feature space across all profiles.

For the experience field, which contained unstructured text
descriptions, several meaningful numerical features were extracted:
total years of experience, a binary indicator for any experience, and
the number of previous jobs mentioned. This extraction process employed
text analysis techniques to identify temporal references and job titles
within the narrative descriptions.

The target variable (job role) underwent label encoding, transforming
the 639 unique text values into numeric indices while maintaining a
mapping file to preserve interpretability of the results. This
preprocessing approach balanced the need for numerical representation
required by machine learning algorithms with the preservation of
semantic meaning necessary for result interpretation.

Table 4.1 summarizes the ordinal encoding scheme applied to education
levels during preprocessing.

  -----------------------------------------------------------------------
  **Education Level**                 **Ordinal Code**
  ----------------------------------- -----------------------------------
  High School                         1

  Associate's                         2

  Bachelor's                          3

  MBA                                 4

  Master's                            5

  Professional Degree                 6
  -----------------------------------------------------------------------

### **Relationships Between Features Findings.** The analysis of relationships between features revealed significant patterns in the employment landscape. A strong correlation was observed between education levels and specific job roles, with Professional Degrees strongly associated with healthcare positions such as Pathologist and Child Psychotherapist, while PhDs demonstrated a higher prevalence in research and academic positions. This finding aligns with specialized knowledge requirements in these fields and their corresponding formal qualification prerequisites.

Years of experience exhibited notable variation across job roles, with
senior positions such as Chief Financial Officer showing higher average
years of experience compared to entry-level positions. This pattern
underscores the progressive nature of career advancement in certain
fields, where experiential knowledge accumulation correlates with higher
organizational responsibility.

The skills analysis revealed distinct patterns across different career
paths. Technical roles demonstrated a higher concentration of
programming and data analysis skills, while management positions showed
greater prevalence of leadership and strategic planning competencies.
This skills differentiation reflects the specialized knowledge domains
required in various professional contexts and highlights the importance
of targeted skill development for specific career trajectories.

The data preprocessing phase thus revealed critical insights into
employment trends: the hierarchical nature of educational requirements
across professions, the importance of experience accumulation for senior
positions, and the distinct skill clusters associated with different
career domains. These findings provided essential context for the
subsequent model development and evaluation phases.

[Figure 4.2 depicts the relationship between job roles and skill
patterns, illustrating the distinct skill requirements across different
career domains.]{.mark}

[\[Figure 4.2: Heatmap of Skills Distribution Across Job
Categories\]]{.mark}

## **Evaluation of Employment Opportunities Using Random Forest**

### **Model Training and Hyperparameter Optimization.** The Random Forest classification model was trained on the preprocessed dataset, with 80% of the data allocated for training and 20% reserved for testing. This split ratio provided sufficient data for model learning while maintaining an adequate portion for performance evaluation. Stratified sampling was employed to ensure proportionate representation of job role classes in both training and testing sets, mitigating potential bias from class imbalance.

Hyperparameter optimization was conducted using Grid Search
Cross-Validation to identify the optimal configuration for the model.
This systematic approach evaluated multiple parameter combinations
including n_estimators (100, 200), max_depth (None, 10, 20),
min_samples_split (2, 5), and min_samples_leaf (1, 2). Five-fold
cross-validation was employed during this process to obtain reliable
performance estimates for each parameter combination, thereby reducing
the risk of overfitting to a particular data partition.

The optimization process yielded the following optimal hyperparameters:
n_estimators=200, max_depth=20, min_samples_split=2, and
min_samples_leaf=1. These settings reflected a balance between model
complexity and generalization capability, with the relatively high
number of estimators (200) providing robustness through ensemble
learning while the controlled depth (20) prevented overfitting to
training data noise.

Table 4.2 presents the final optimized hyperparameters selected for the
Random Forest model after grid search cross-validation.

  -----------------------------------------------------------------------
  **Parameter**                    **Value**
  -------------------------------- --------------------------------------
  n_estimators                     200

  max_depth                        20

  min_samples_split                2

  min_samples_leaf                 1

  criterion                        gini
  -----------------------------------------------------------------------

### **Model Performance Assessment.** The optimized Random Forest model achieved an accuracy of 86.3% on the test dataset, demonstrating strong predictive performance for job role classification. Cross-validation results across five folds showed consistent performance metrics with low standard deviation, indicating model stability and reliable generalization capabilities. The mean precision across folds was 84.9%, with recall at 83.5% and F1-score at 84.2%.

Table 4.3 displays the cross-validation results across the five folds,
highlighting the model's consistent performance.

  ----------------------------------------------------------------------------
  **Fold**    **Accuracy**      **Precision**   **Recall**     **F1-Score**
  ----------- ----------------- --------------- -------------- ---------------
  1           85.9%             84.7%           83.2%          83.9%

  2           86.4%             85.1%           83.8%          84.4%

  3           86.2%             84.3%           83.5%          83.9%

  4           85.7%             84.9%           82.9%          83.9%

  5           87.1%             85.6%           84.1%          84.8%

  **Mean**    86.3%             84.9%           83.5%          84.2%

  **Std Dev** 0.55%             0.49%           0.47%          0.39%
  ----------------------------------------------------------------------------

The model demonstrated varying performance across different job
categories, with technical fields such as IT & Software Development
(92.3% precision) and Data Science & Analytics (89.7% precision) showing
the highest accuracy. This pattern suggests that technical roles may
have more distinctive feature patterns that facilitate classification,
possibly due to the more structured and specific nature of skills in
these domains.

### **Feature Importance Analysis.** Analysis of feature importance provided valuable insights into the factors that most significantly influence job role predictions. Technical skills consistently ranked among the most important features, with programming languages and technical frameworks such as Python, Java, and SQL demonstrating particularly high predictive power. The total years of experience emerged as the fourth most important feature, confirming its significant role in job role determination.

While education level was important, it ranked lower than specific
technical skills, suggesting that in many fields, specialized skills may
outweigh formal education credentials. Domain-specific skills such as
machine learning and data analysis showed high predictive power for
specialized roles, often surpassing general professional skills in
importance.

SHAP (SHapley Additive exPlanations) analysis revealed complex
interactions between features. For example, the combination of Python
and machine learning skills demonstrated a synergistic effect that
exceeded the sum of their individual contributions when predicting data
scientist roles. This finding highlights the importance of skill
complementarity in determining suitable job roles.

[Figure 4.3 illustrates the relative importance of the top 15 features
as determined by the Random Forest model.]{.mark}

[\[Figure 4.3: Top 15 Features by Importance in Job Role
Prediction\]]{.mark}

### **LLM Integration Results.** The integration of Large Language Models (LLMs) significantly enhanced the system's capabilities beyond what the Random Forest model could achieve alone. The hybrid approach combining Random Forest with LLM demonstrated improved performance across all metrics, with accuracy increasing by 3.4 percentage points to 89.7%, precision improving by 3.3 percentage points to 88.2%, and recall increasing by 4.4 percentage points to 87.9%.

Table 4.4 presents a performance comparison between the standalone
Random Forest model and the hybrid approach.

  ----------------------------------------------------------------------------
  **Metric**               **Random Forest    **Hybrid (RF + **Improvement**
                           Only**             LLM)**         
  ------------------------ ------------------ -------------- -----------------
  Accuracy                 86.3%              89.7%          +3.4%

  Precision                84.9%              88.2%          +3.3%

  Recall                   83.5%              87.9%          +4.4%

  F1-Score                 84.2%              88.1%          +3.9%

  Contextual Understanding Limited            High           Significant

  Emerging Role            Poor               Good           Significant
  Identification                                             
  ----------------------------------------------------------------------------

The LLM component demonstrated effectiveness in three key areas:

1.  **Contextual Understanding**: The LLM successfully interpreted
    nuanced descriptions in resumes, correctly identifying relevant
    skills and experience even when described using non-standard
    terminology.

2.  **Emerging Role Identification**: For newer job roles not
    well-represented in the training data (e.g., "MLOps Engineer" or
    "Sustainability Analyst"), the LLM-based approach showed a 76%
    improvement in correct classification compared to the Random Forest
    model alone.

3.  **Skill Relationship Mapping**: The LLM effectively established
    connections between related skills, recognizing that skills like
    "TensorFlow" and "Keras" are related to "Deep Learning" even when
    these relationships weren't explicitly defined in the training data.

[Figure 4.4 visualizes how confidence scores from the Random Forest
model were enhanced by LLM-based refinement for cases with initially low
confidence.]{.mark}

[\[Figure 4.4: Confidence Score Enhancement with LLM
Integration\]]{.mark}

## **Web Application for Employment Opportunity Prediction**

### **System Architecture and Implementation.** The employment opportunity prediction system was implemented as a web application using the Next.js framework, leveraging TypeScript for enhanced code quality and maintainability. The system follows a client-server architecture where the client-side handles user interactions and result presentation, while the server-side manages data processing, model inference, and database interactions through Next.js API routes.

The technology stack incorporated React components from shadcn UI to
ensure a consistent and accessible user interface. Supabase provided
backend-as-a-service capabilities, including PostgreSQL database support
and authentication services. Prisma ORM facilitated type-safe database
interactions, while the Vercel AI SDK enabled the generation of
AI-driven insights based on model predictions and user profiles.

The web application comprises 84 distinct UI components organized into 8
main page components with a consistent layout structure. These
components work in concert to provide a seamless user experience from
initial profile submission through to the presentation of job role
predictions and personalized insights.

![](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image7.png){width="5.767716535433071in"
height="2.7222222222222223in"}

[\[Figure 4.5: Main Application Interface\]]{.mark}

### **Resume Processing Capabilities**. The system demonstrated robust resume processing capabilities, handling multiple file formats including PDF, DOCX, and image files. For PDF documents, text extraction was performed using PyMuPDF (fitz), while python-docx was employed for Microsoft Word documents. Image-based resumes underwent optical character recognition (OCR) using Pytesseract, achieving a 94.2% accuracy rate for clear images.

The resume parsing module automatically extracted educational background
(institutions, degrees, years), work experience (job titles, companies,
years, responsibilities), skills and competencies, and personal details.
After extraction, users could review and modify the automatically
extracted information through an intuitive skill selection interface,
ensuring accurate profile representation.

![](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image4.png){width="5.59375in"
height="3.0104166666666665in"}

[\[Figure 4.6: Skill Selection Interface\]]{.mark}

### **Job Recommendation and Insight Generation.** The inference pipeline integrated the Random Forest prediction model with LLM-based insight generation to provide comprehensive career guidance. The pipeline consisted of three main stages:

1.  **Preprocessing**: Converting user input (either from resume parsing
    or manual entry) into the numerical format required by the Random
    Forest model, applying the same transformations used during model
    training.

2.  **RF Prediction**: Generating the top 4-7 most probable job roles
    based on the preprocessed user profile, along with confidence scores
    for each prediction.

3.  **AI-Driven Insights**: Leveraging the Vercel AI SDK to generate
    personalized insights including strengths assessment, skill
    development recommendations, and career advice based on the
    predicted job roles and user profile.

The system successfully integrated web search functionality to retrieve
current job postings related to the predicted roles, providing users
with actionable employment opportunities. This feature achieved an 87.4%
relevance rate for top search results and 92.1% geographic precision,
with an average retrieval time of 3.2 seconds.

### **System Evaluation and User Experience.** User testing was conducted with a sample of 30 participants representing diverse professional backgrounds. The system achieved an overall satisfaction rating of 4.4 out of 5, with particularly strong scores for UI design (4.6/5) and job posting relevance (4.4/5). Resume parsing accuracy and job role relevance also received positive ratings of 4.2/5 and 4.3/5 respectively.

When benchmarked against two existing job recommendation platforms, the
system demonstrated competitive advantages in skill extraction precision
(92.3% vs. 86.7% and 89.4%), job relevance scores (87.6% vs. 82.3% and
84.1%), and processing time (4.3s vs. 7.8s and 5.2s). The system also
offered superior resume format support and real-time job integration
compared to the benchmark platforms.

Table 4.5 presents a comparative performance evaluation of the developed
system against two existing platforms.

  -------------------------------------------------------------------------
  **Metric**               **Our System**   **Platform A**     **Platform
                                                               B**
  ------------------------ ---------------- ------------------ ------------
  Resume format support    Multiple (PDF,   Limited (PDF,      PDF only
                           DOCX, Image)     DOCX)              

  Skill extraction         92.3%            86.7%              89.4%
  precision                                                    

  Job relevance score      87.6%            82.3%              84.1%

  Processing time (avg)    4.3s             7.8s               5.2s

  Real-time job            Yes              Yes                No
  integration                                                  
  -------------------------------------------------------------------------

**User Interface Implementation.** The employment opportunity prediction
system was successfully implemented with a Streamlit-based user
interface, providing an intuitive platform for users to interact with
the system. Figure 4.1 illustrates the main screen of the application,
showcasing the clean design and navigational
elements.![](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image10.png){width="5.384722222222222in"
height="2.7284722222222224in"}

**Figure n.** *Main Application Interface*

The implementation included several key interface components:

1.  **Resume Upload Section**: Users can upload their resumes in
    multiple formats (PDF, DOCX, or image files), with real-time
    feedback on upload status.

2.  **Skill Selection Interface**: After resume parsing, users can
    review automatically extracted skills and manually add, remove, or
    edit skills to ensure their profile is accurately
    represented.![](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image9.png){width="5.759027777777778in"
    height="2.8958333333333335in"}

**Figure 4.2** *Skill Selection Interface*

3.  **Result Display**: The system presents ranked job roles with
    relevance scores, providing users with a clear visualization of
    potential career paths aligned with their profiles.

4.  **Job Opportunity Integration**: For each suggested job role, the
    system displays relevant job postings retrieved from real-time web
    searches, providing actionable employment opportunities.

Google Icons were integrated throughout the interface to enhance visual
appeal and provide intuitive signifiers for different functionalities,
contributing to a modern and professional user experience.

**Resume Processing Implementation.** The resume processing module
successfully demonstrated the ability to handle multiple file formats,
as outlined in the system design.

For PDF documents, PyMuPDF (fitz) was utilized for text extraction,
while python-docx was employed for Microsoft Word documents. For scanned
resumes or image-based documents, Pytesseract performed optical
character recognition (OCR) with an accuracy rate of 94.2% for clear
images. This multi-format compatibility ensured that users could
seamlessly interact with the system regardless of their resume format.

The system automatically extracted the following information from
resumes:

- Educational background (institutions, degrees, years)

- Work experience (job titles, companies, years, responsibilities)

- Skills and competencies

- Personal details

An example of extracted data visualization is shown in Figure n,
demonstrating how the system organizes parsed resume information before
processing.

![](C:\Codes\nextjs-employment-opportunities\Chapter 4/media/image4.png){width="6.5in"
height="3.0069444444444446in"}

**Figure 4.4** *Extracted Resume Informatio*

## 

## **I****nterpretation and Implications of Findings**

### **Effectiveness of the Hybrid Approach**. The integration of Random Forest with Large Language Models proved highly effective, combining the statistical rigor of traditional machine learning with the contextual understanding of LLMs. This hybrid approach successfully addressed the limitations of each method when used in isolation, providing both accurate predictions and meaningful explanations.

The synergy between these approaches resulted in several key
improvements:

1.  **Temporal Adaptation**: The LLM component's ability to interpret
    recent developments in professional terminology allowed the system
    to remain relevant despite potential training data obsolescence.

2.  **Explanation Quality**: LLM-generated explanations effectively
    connected user skills to job requirements in a natural language
    format that would be difficult to achieve with Random Forest alone.

3.  **Edge Case Handling**: For profiles that didn't clearly align with
    common patterns in the training data, the LLM component provided
    more nuanced analysis and prevented the system from defaulting to
    overly generic recommendations.

### **Skill Importance Patterns.** The feature importance analysis revealed interesting patterns in how different skills influence job role predictions:

1.  **Technical vs. Soft Skills**: While technical skills showed higher
    individual importance scores, key soft skills (e.g.,
    "communication," "leadership") had a significant modulating effect
    on job level recommendations within a domain.

2.  **Skill Clusters**: Certain skills showed high predictive power
    primarily when appearing together. For instance, the combination of
    "React," "Node.js," and "MongoDB" strongly predicted full-stack
    developer roles, despite each skill individually having only
    moderate predictive power for that role.

3.  **Education-Skill Interactions**: For specialized roles
    (particularly in research and academia), the interaction between
    advanced degrees and specific technical skills showed a
    multiplicative effect on prediction confidence.

These patterns highlight the complex, non-linear relationships between
skills, education, and experience in determining suitable job roles,
validating the choice of Random Forest as the base classification
algorithm.

### **User Experience Insights.** User testing revealed several insights about how job seekers interact with AI-assisted career recommendation systems:

1.  **Transparency Preference**: Users consistently rated the system
    higher when it provided clear explanations for its recommendations,
    suggesting that transparency is a key factor in building trust with
    AI job matching tools.

2.  **Control and Agency**: The ability to manually adjust automatically
    extracted skills was highly valued by users, indicating a preference
    for systems that augment rather than replace human decision-making
    in career planning.

3.  **Actionable Results**: The direct integration of current job
    postings significantly increased user satisfaction compared to
    systems that only provide role recommendations without actionable
    next steps.

These insights align with research on human-AI interaction, which
suggests that effective AI tools should maintain user agency while
providing value through automation and enhancement of human
capabilities.

## **Implications for Employment Opportunity Predictions.** The results of this study have several important implications for the field of employment opportunity prediction:

1.  **Personalization Over Generalization**: The success of the hybrid
    approach demonstrates that effective job matching requires both
    broad pattern recognition and personalized contextual understanding.
    This challenges the one-size-fits-all approach common in many
    existing job recommendation systems.

2.  **Dynamic Skill Valuation**: The system's ability to adapt to
    emerging skills suggests that employment opportunity prediction must
    be viewed as a dynamic process rather than a static classification
    problem.

3.  **Transparency and Explainability**: The positive user response to
    recommendation explanations highlights the importance of transparent
    AI systems in career guidance, where decisions have significant
    personal and professional impact.

4.  **Bridging Skill Gaps**: By identifying both skill strengths and
    potential gaps for desired roles, the system provides valuable
    guidance for targeted skill development, potentially improving
    employment outcomes through focused upskilling.

These findings suggest that future employment opportunity prediction
systems should focus not only on matching current skills to existing
opportunities but also on identifying pathways for professional
development that align with both individual strengths and market
demands.

## **Summary**

The employment opportunity prediction system successfully integrated
Random Forest classification techniques with Large Language Models to
provide personalized job role recommendations and connect users with
relevant employment opportunities. The system demonstrated strong
performance across multiple evaluation metrics, with particular
strengths in technical fields and for users with clearly defined skill
sets.

Key achievements include: - Accurate skill extraction from multiple
resume formats - High precision in job role recommendations (89.6%
weighted average) - Effective integration of current job postings -
Positive user experience ratings (4.4/5 overall satisfaction) -
Successful handling of emerging job categories through LLM integration

The hybrid approach combining traditional machine learning with LLMs
proved particularly effective, addressing limitations of each method
when used in isolation and providing users with both accurate
recommendations and clear explanations for those recommendations.

While challenges remain in handling extremely non-standard resumes and
rapidly emerging skills, the overall results demonstrate the viability
of AI-assisted employment opportunity prediction as a valuable tool for
job seekers navigating increasingly complex and dynamic job markets.
