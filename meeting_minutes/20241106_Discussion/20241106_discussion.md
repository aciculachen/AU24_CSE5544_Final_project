# 5544 Group Project - Implementations

Due: December 3, 2024

## Our Reports

- [https://docs.google.com/document/d/14TjZFSQSjO3fLISfRxgAiA8KIHq1tJQkHboM_WqCHxM/edit?tab=t.0](https://docs.google.com/document/d/14TjZFSQSjO3fLISfRxgAiA8KIHq1tJQkHboM_WqCHxM/edit?tab=t.0)

## References

- Interactive website: Visualized results (from University of Konstanz): [https://mc3-1.vast23.dbvis.de/home](https://mc3-1.vast23.dbvis.de/home)
- Papers: https://github.com/yzhao062/anomaly-detection-resources
- **AnchoVis: Visual Analytics for Combating Illegal Fishing by Detecting Anomalous Structures 🎣:** https://github.com/IDCLab-VAST-Challenge-2023/AnchoVis
- https://github.com/PostSonne/vast-challenge-2023-mc3

- [VAST Challenge 2023 UKON-Grotzeck-MC3](https://www.youtube.com/watch?v=pH1kWyor5OM)

---

## Thoughts & Implementations

- VAST challenge MC3 problem set
    - Develop a visual analytics process to find similar businesses and group them. This analysis should focus on a business’s most important features and present those features clearly to the user.
    - Measure similarity of businesses that you group in the previous question. Express confidence in your groupings visually.
    - Based on your visualizations, provide evidence for or against the case that anomalous companies are involved in illegal fishing. Which business groups should FishEye investigate further?
1. Do we need to preprocess data, i.e. filter out some unrelated nodes?
    - No, I don’t think so.
2. Can we visualize data from different perspectives and provide interactive charts to users to analyze the companies?
    - Our criteria
        - Companies that have missing attributes (such as beneficial owners), unusual revenue, or unusual numbers of the roles that a node plays
        - Nodes that have too many connections or no connections, e.g. isolated nodes.
        - The same beneficial owner owns companies, or vice versa.
3. Possible pipeline for us:
    - Phase 1: Visualize all node relationships from different perspectives to find business similarities and group them. For example, a user can narrow the datasets down to a specific part by industry and look into the details. Possible perspectives are:
        - Categorize companies by the amount of revenue 
            - Purpose: By doing so, users can take a detailed look at high-revenue companies for illegal services. (Out of my instinct)
            - Find companies that are owned by the same beneficial owners
                - x: beneficial owners; y: the number of companies; heatmap-value: companies
        - Companies are categorized by industry based on the `product_services` attribute. Possible charts are:
            - Actions: How do we categorize companies by industry? AI?
            - Find companies with unusual revenue compared to other companies in the industry. **Expected result: ??**.
                - x: revenue; y: the number of companies; heatmap-value: companies
                - interactive actions: click the block and display companies 
            - Find companies with unusual revenue compared to other companies in the same country. **Expected result: ??**
                - x: revenue; y: countries; heatmap-value: # of companies
                - interactive actions: click the block and display companies 
            - Find companies with unusual revenue compared to other companies in the same product service
                - x: revenue; y: product service; heatmap-value: # of companies
                - interactive actions: click the block and display companies 
        - Display information about the selected companies: beneficial owners and company contacts
        - Keep suspicious companies and analyze them later
    - Phase 2: Visualize the relationship between the suspicious companies
        - Questions:
            - How do we identify companies that are excluded from the analyzed charts because they missed some attributes?
        - Possible actions
            - Develop a metric to find hidden companies with similar structures. The disadvantage for users is that they have to investigate the anomalies company by company.
                - Any better way?
            - Any others?

## Techniques

- Python for data preprocessing
- D3
    - Rendering on the web page
- Tableau: A desktop tool. An analytic tool. Easy to use. Interactive display.