## A Recommender System for Investing in Early-Stage Enterprises: A Detailed Analysis

This paper proposes a recommender system for investors seeking to invest in early-stage enterprises (ESEs). It combines a rigorous requirements analysis with an evaluation of various recommendation algorithms, aiming to provide a system that effectively assists investors in identifying promising ESEs.

### 1. Introduction and Research Questions

The paper addresses the challenge faced by investors in selecting suitable ESEs, particularly when information is scarce. The authors aim to design, implement, and evaluate a system that provides personalized recommendations.

The paper explores three main research questions:

1. **What are the requirements for a recommender system for investment in ESEs?**
2. **What are the different recommendation approaches for this domain?**
3. **How do different recommendation approaches perform in practice?**

### 2. Background

The paper establishes a foundation by defining key concepts relevant to the domain:

**Early-Stage Enterprises (ESEs):** 
* These are young companies in the seed or start-up stages, focused on product development and market analysis.
* They typically operate at a loss and require external funding to reach profitability.

**Funding:**
* ESEs rely on internal funding (founders, family, friends) and external funding (public agencies, investors).
* Investors, particularly business angels (BAs) and venture capital (VC) firms, play a crucial role in providing financial and intangible support.

**Valuation:**
* The process of determining an ESE's worth based on its future potential.
* ESE valuation methods primarily consider future prospects and employ techniques like the Scorecard and Berkus methods.

**Recommender Systems:**
* Systems that suggest items (e.g., products, news) based on user profiles and item content.
* Existing recommender systems in finance focus on portfolio selection and stock recommendations, but none explicitly cater to ESE investment.

### 3. Requirements Analysis

The authors conducted a two-phase requirements analysis to understand investors' needs and preferences:

**Qualitative Study:**
* Conducted in-person interviews with six prominent investors from the DACH region (Germany, Austria, Switzerland).
* Investigated decision criteria for investing in ESEs and expectations from a recommendation platform.

**Key findings:**
* Investors prioritize value proposition, product maturity, team experience, and risk awareness.
* They consider trust relationships with other investors and value the opinions of experts.
* Expectations for a recommendation platform include personalized profiles, valuation support, market analysis, and trust-based recommendations.

**Quantitative Study:**
* Surveyed 25 investors, focusing on their decision criteria, desired functionalities, and valuation methods.
* Used the Wilcoxon Signed Rank test to assess the statistical significance of responses.

**Key findings:**
* Confirmed the importance of team experience, industry sector, market research, return on investment vs. risk, and recommendations from other investors.
* Highlighted the importance of characteristics like opportunity, product maturity, customer acceptance, industry structure, competition, and team experience in ESE valuation.
* Identified "filtering early-stage enterprises according to personal preferences," "visualization of pre-money valuations," and "visualization of the founder team's experience" as crucial functionalities.

**Five specific requirements derived from the analysis:**

**R1. Valuations of ESEs:**  The system should support the Scorecard and Berkus methods for valuation and allow retrieval of existing valuations.
**R2. Information on ESEs and target market:**  The system should provide information about the ESE's team, product, and market sector.
**R3. Investor Profiles:**  The system should enable investors to build detailed profiles capturing their interests and preferences and support the retrieval of matching ESEs.
**R4. Historical Investment Decisions:**  The system should leverage past investment behavior when making recommendations.
**R5. Trust among Investors:**  The system should consider opinions of trusted investors when making recommendations.

### 4. Recommender System Design

The authors propose a recommender system fulfilling the outlined requirements, consisting of data entities and recommendation algorithms:

**Data Entities:**

* **Enterprise (Item):** ESEs are the items being recommended.
* **Enterprise Description:** Includes attributes like name, location, product description, investment options, valuations, market sector, team members, and roles.
* **Entrepreneur:** The user responsible for maintaining an ESE's information in the system.
* **Valuator:** The user who creates valuations using the Scorecard or Berkus methods.
* **Investor (User):** The end-user receiving recommendations.
* **Investor Profile:** Captures investor preferences across attributes like market sectors, product descriptions, investment amount, valuation, life cycle, team size, etc. Users can define the relative importance of each attribute.
* **User-Item Interactions:** The system collects data on investor clicks, likes, and investments, providing insights into user behavior.

**Recommendation Algorithms:**

The system implements five distinct algorithms, each addressing specific requirements:

* **Knowledge-Based (KB):** This algorithm matches ESEs to investors based solely on profiles and descriptions. It uses filters as hard constraints and preferences as soft constraints to rank ESEs based on weighted Borda counts.
* **Content-Based (CB):** This algorithm creates a "virtual" enterprise based on an investor's historical interactions and compares ESEs to it using Jaccard similarity.
* **Collaborative Filtering (CF):** This algorithm exploits user-item interactions. 
    * **User-Based CF (CF-UB):**  Calculates similarity between investors based on their interaction history and recommends ESEs based on their neighbor's preferences. 
    * **Item-Based CF (CF-IB):**  Calculates similarity between ESEs based on investor interactions and recommends ESEs based on their similarity to ESEs the investor has previously liked or invested in.
* **Social-Based (SB):** This algorithm explicitly leverages trust relationships between investors, using a user-based CF approach with explicitly defined neighborhoods.
* **Hybrid (HB):** This algorithm combines the knowledge-based and user-based collaborative filtering approaches. It calculates similarity between investors based on the rankings generated by their KB profiles.

### 5. Evaluation

The authors conduct an offline evaluation using a small dataset collected through a questionnaire from 35 investors:

**Data Collection:**

* Collected information on investor profiles, trust relationships, and preferences for a set of 10 ESEs.
* Used a Likert scale to capture the importance of various attributes for investment decisions.
* Created a directed graph depicting the trust network among investors.
* Ranked ESEs based on investor preferences.

**Data Preparation:**

* Processed the collected data to create investor profiles, trust relationships, and historical interaction data.
* Partitioned the data into training and testing sets using leave-one-out cross-validation.

**Evaluation Methodology:**

* Measured the correlation between recommendation lists using Spearman rank correlation.
* Calculated ranking accuracy metrics, including Precision@k, Mean Average Precision@k (MAP@k), and Normalized Discounted Cumulative Gain@k (nDCG@k), to assess the performance of different algorithms.

**Key Findings:**

* Item-based approaches (CF-IB and CB) performed poorly, suggesting historical decisions are not strong predictors of future preferences.
* The knowledge-based approach (KB) did not consistently outperform the content-based approach (CB), implying explicit preference capture may not be more helpful than observing behavior.
* User-based approaches (CF-UB and SB) performed best, with SB outperforming CF-UB. This supports the idea that trust relationships are more reliable than implicit similarity derived from interactions.
* The hybrid approach (HR) performed worse than its base algorithms (KB and CF-UB), indicating that profile-based similarity is less effective than interaction-based similarity.

**Discussion:**

* The study highlights the importance of trust relationships in ESE investment recommendations.
* The limited dataset size and geographical bias are limitations that could affect the evaluation results.

### 6. Conclusion

The paper concludes that collaborative filtering approaches, especially trust-based ones, are more effective than knowledge-based and content-based approaches in the domain of ESE investment recommendations. 

The authors emphasize the importance of further research with larger datasets and a wider range of investors to refine the recommender system and explore other potential recommendation strategies.

### Code Snippets and Formulas (LaTeX):

* **Jaccard Similarity:**
```latex
Jaccard(A, B) = \frac{|A \cap B|}{|A \cup B|}
```

* **User-Based Collaborative Filtering (CF-UB) Formula:**
```latex
s(u,i)=\frac{\sum_{u^{\prime}\in N(u)}sim(u,u^{\prime})\cdot r(u^{\prime},i)}{ \sum_{u^{\prime}\in N(u)}sim(u,u^{\prime})} 
```
Where:
* \(s(u,i)\) is the chance of user \(u\) liking item \(i\).
* \(N(u)\) is the neighborhood of user \(u\).
* \(sim(u,u^{\prime})\) is the similarity between user \(u\) and \(u^{\prime}\).
* \(r(u^{\prime},i)\) is the rating user \(u^{\prime}\) gave to item \(i\).

### Tables and Figures:

* **Table 1: Ranking Correlation**
* **Table 2: Ranking Accuracy Metrics**
* **Figure 1: Investment Criteria**
* **Figure 2: Enterprise Characteristics**
* **Figure 3: Recommendation Criteria**
* **Figure 4: Recommendation Functionality**
* **Figure 5: Distribution of Answers for Likert-Type Questions**
* **Figure 6: Investor Trust Network**
* **Figure 7: Distribution of Ranks Assigned to Early-Stage Enterprises**

### Overall Methodology:

* The authors adopt a design science research methodology, focusing on the development of a practical solution for a real-world problem.
* They leverage a mixed-method approach combining qualitative and quantitative research methods to gather requirements.
* The evaluation is conducted using an offline experiment with a small dataset collected through a questionnaire.

This comprehensive analysis provides valuable insights into the design and evaluation of recommender systems for ESE investment. The findings suggest that incorporating trust relationships and user behavior is crucial for achieving accurate and personalized recommendations. 
