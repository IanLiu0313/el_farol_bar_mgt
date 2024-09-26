# README

- This is code can be run locally, or on Google Colab
    - If run on Google Colab, change the directory to your own Google Drive, and set if Colab == TRUE.
    - If run on your own device, change the directory and call the .py file in Terminal/Command Prompt
- Introduction: this code simulates a dynamic market environment where industries and companies evolve over time, based on the El Farol bar problem. Each industry is preset to experience 4 stages: emergence, growth, maturity, and decline. The same pattern also applies to companies within these industries. For now, industries and companies are randomly generated. Modifications will be made later according to the literature review results.
- Code implementation:
    - Market Size: the market is defined as a 500x500 unit grid.
    - **class Company** has all settings/attributes about the the companies
        - initial_industry: the industry the company belongs to.
        - scale: company's size.
        - competitiveness: a factor contributing to growth rate.
        - uncertainty: noise
        - profitability: each industry stage leads to a different value
        - x & y: coordinates to locate a company within the industry.
    - Industry Lifecycle Stages: emergence, growth, maturity, decline. Each stage affects the industry's radius and, consequently, the companies within it. **This is a very beyond naive implementation, I’m reading papers to find how industries and companies are actually behaving.**
    - Important Functions
        - def update_industries(industries, companies)
            - Updates each industry's age, stage, and radius.
            - Adjusts profitability for companies based on the industry's current stage.
        - def update_companies(companies, industries)
            - Updates each company's scale considering competitiveness, profitability, and uncertainty.
            - Ensures company scale does not exceed the industry's area.
        - def is_far_enough(new_industry, industries, min_distance
            - Checks that a new industry is sufficiently distant from existing ones.
        - def create_new_industry(market_size, industries)
            - Generates a new industry with random position and attributes.
            - Ensures it's within market boundaries and not too close to others.
        - def create_companies_for_industry(industry)
            - Creates a random number of companies (1-5) within an industry.
            - Assigns random scale, competitiveness, and uncertainty to each company.

- How is the program designed?
    1. Initialization
        1. Starts with a single industry created by calling create_new_industry()
        2. Initializes companies within this industry using create_companies_for_industry()
    2. Simulation Loops
        1. The animate() function is called repeatedly to simulate time steps.
        2. At each step: 
            1. With a 20% chance, a new industry is added to the market.
            2. Updates company and industry
            3. Deletes the old or diminished industries and companies in them
            4. Makes the animated plot and saves locally