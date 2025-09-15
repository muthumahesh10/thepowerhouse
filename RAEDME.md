🏠 Power House Insulation - Company Website
🚀 Project Overview
This repository contains the complete code for the Power House company website. It is a modern, single-page web application designed to serve as a comprehensive tool for both marketing and customer engagement. The primary goal of the website is to educate potential customers in India about the financial, comfort, and environmental benefits of professional insulation, and to generate qualified leads through an interactive savings calculator and a quote request form.

The entire website is contained within a single index.html file, which includes all necessary HTML, CSS (via Tailwind CSS), and JavaScript.

Website Structure & Features
The website is designed as a single-page application with distinct sections that function as different pages.

1. 🏠 Home Tab
This is the main landing page. Its purpose is to capture the user's attention and provide immediate value.

Hero Section: A visually appealing introduction with a clear value proposition: "Lower Your Bills, Help the Planet." 💸🌍

Insulation Calculator: 🧮 An interactive tool allowing users to get an instant estimate of their potential financial savings, energy savings, and environmental impact.

Product Filter: 🔎 An interactive section allowing users to filter and find the perfect insulation product based on properties, construction type, and application area.

Tariff Chart: 📊 A graph showing the rising costs of electricity in India to create a sense of urgency.

Core Services & Why Choose Us: A quick overview of what Power House offers and its key strengths.

2. 🤔 Why Insulation? Tab
This section is designed to educate the customer in detail.

Data-Driven Arguments: 📈 It features charts and data on rising electricity tariffs and carbon emissions to build a strong, evidence-based case for insulation.

Source Links: All data is backed by credible source links to government and international agencies.

Detailed Benefits: Expands on the core benefits like cost savings, year-round comfort, soundproofing, and property protection.

3. 🛠️ Our Services Tab
This tab clearly outlines the specific services offered, categorized for easy understanding.

Residential Insulation: Services for homes, including roofs, walls, and acoustic solutions.

Commercial & Industrial Insulation: Solutions for businesses, offices, warehouses, and industrial facilities.

4. 📝 Get a Quote Tab
This is the primary lead-generation tool. It's a simple, user-friendly form that allows potential customers to request a formal, no-obligation quote. The form is configured to work with the Formspree.io service to deliver submissions to your email.

5. 📞 Contact Us Tab
Provides all necessary contact information, including email, phone number, a link to your LinkedIn profile for technical inquiries, and business hours.

The Insulation Calculator: How It Works 🧮
The calculator is the most complex feature of the website. It uses a multi-layered formula to provide a holistic estimate of the benefits of insulation.

1. How the Estimated Project Cost is Calculated 💰
The cost is based on the area of insulation and a dynamic price-per-square-foot.

Formula: Total Area (sq. ft.) × Final Cost Per Square Foot

Base Cost (costPerSqFt): The calculation starts with a base price which is determined by the Climate Zone and the Area to Insulate (roofs are more expensive than walls).

Adjustment Factors: This base cost is then modified by several percentage multipliers:

Building Type: +10% for Commercial properties.

Roof Type: +15% for Pitched/Sloped roofs.

Existing Insulation: -20% if insulation already exists.

2. How Financial & Energy Savings are Calculated ⚡
The savings calculation is dynamic, prioritizing the most accurate data provided by the user.

Savings Percentage (savingsPercentage): A base savings percentage is set based on Climate Zone and Area to Insulate. This is then adjusted by:

Building Type: +5% for Commercial properties.

Building Age: Older buildings have a higher savings potential (from +5% up to +20%).

Existing Insulation: Savings potential is reduced by 60% if some insulation already exists.

Annual Financial Savings: (Avg. Monthly Electric Bill × 12) × Final Savings Percentage.

Annual Energy Savings (kWh): The calculator uses one of two methods:

If 'Avg. Power (Watts)' is entered: It uses this more precise data to calculate the total annual energy consumption and then applies the Final Savings Percentage. This is the more accurate method.

If 'Watts' is left blank: It estimates the kWh saved by dividing the Annual Financial Savings by an average cost of electricity in India (AVG_KWH_PRICE_INDIA).

3. How Carbon Reduction is Calculated 🌳
This translates the energy savings into a tangible environmental impact.

Carbon Reduction (kg CO₂): Annual Energy Savings (kWh) × INDIA_KWH_TO_CO2_KG. This uses a standard emissions factor for electricity generated in India.

Trees Equivalent: The total CO₂ reduction is divided by the average amount of CO₂ a mature tree absorbs in a year (22 kg).

How to Update Calculator Prices (Market Movements) 💹
To keep your calculator accurate, you will need to update its pricing variables as market conditions change. You only need to edit the index.html file.

Step 1: 📂 Open index.html in a simple text editor.

Step 2: 🔍 Search for the function calculateAndShowResults() in the <script> section at the bottom of the file.

Step 3: ✏️ Inside this function, you will find all the variables you need to change.

To Change Base Prices & Savings:
Locate this code block. Simply change the number after costPerSqFt = for price, and savingsPercentage = for savings potential.

// ...
let costPerSqFt = 50; 
let savingsPercentage = 0.25; 

if (areaType === 'roof') {
    if (cityZone === 'hot-dry' || cityZone === 'warm-humid') { costPerSqFt = 75; savingsPercentage = 0.35; } 
    else if (cityZone === 'composite') { costPerSqFt = 70; savingsPercentage = 0.30; } 
    // ... etc.
}

To Change Adjustment Percentages:
Locate this block. The numbers are multipliers (1.1 is a 10% increase, 0.8 is a 20% decrease).

// ...
if (buildingType === 'commercial') { costPerSqFt *= 1.1; savingsPercentage *= 1.05; }
if (areaType === 'roof' && roofType === 'pitched') { costPerSqFt *= 1.15; }
if (existingInsulation === 'yes') { savingsPercentage *= 0.4; costPerSqFt *= 0.8; }
// ... etc.

To Change Environmental Constants:
Locate these lines to update the average electricity price or the CO₂ conversion factor based on new national data.

// ...
const INDIA_KWH_TO_CO2_KG = 0.82; 
const AVG_KWH_PRICE_INDIA = 7.5; 
// ...

After editing and saving the file, your calculator will immediately use the new values.
