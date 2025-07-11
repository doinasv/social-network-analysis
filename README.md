# 🌐 Social Network Analysis of World Import Trade (2022)

This project applies **Social Network Analysis (SNA)** to explore the structure of global trade in 2022, using import data from the **World Bank**. Countries are treated as nodes, and import flows as directed, weighted edges. The goal is to uncover the most influential economies, regional trade patterns, and structural dependencies in international commerce.

---

## 📦 Dataset

- **Source**: [World Bank – Market Composition & Growth (Import)](https://datacatalog.worldbank.org/)
- **Year**: 2022
- **Size**: ~8.2 million rows
- **Key fields**:
  - `ReporterISO3`: Importing country
  - `PartnerISO3`: Exporting country
  - `TradeValue_EndYear`: Value of trade in USD

---

## 🧹 Data Cleaning & Preprocessing

The project's focus is on **country-level trade relationships** — not product-level detail. Therefore:

- The dataset was **grouped by country pairs**, and trade values were **summed across all product types**
- The final structure includes only:
  - `ReporterISO3` (importing country)
  - `PartnerISO3` (partner/exporting country)
  - `TradeValue_EndYear` (total import value)
- Duplicate rows were removed so **each unique country pair appears only once**

This transformation simplifies the network while preserving the full scope of bilateral trade activity.

**Tool used**: `pandas`

---

## 🌐 Network Construction

A **directed graph** is constructed to reflect the flow of goods:
- **Nodes**: Countries
- **Edges**: Import relationships, directed from **exporter → importer**
- **Weights**: Represent total import value

The directionality is crucial for modeling the dependency of one country on another’s exports. This network enables exploration of complex trade structures and geopolitical clusters.

**Tools used**: `networkx`, `matplotlib`, `cartopy`

---

## 🧠 Centrality Analysis

To assess each country’s influence and connectivity within the global trade network, the following centrality measures are calculated:

- **Degree centrality**
- **Closeness centrality**
- **Betweenness centrality**
- **Weighted eigenvector centrality**

These metrics are well-suited for trade network analysis (Antonietti et al., 2022) and reveal both direct and indirect power within the system.

---

## 📊 Key Insights

- The **United States** was the top importer in 2022, followed by **China**
- The largest economies tend to import from other top importers, suggesting strong mutual infrastructure and trade agreements
- **Neighboring countries** (e.g., US–Mexico–Canada, or European trading blocs) often appear as each other’s top partners
- Countries with high **closeness** also tend to score high in **eigenvector centrality** — showing both accessibility and influence  
  *(Sugita, Teshima & Seira, 2021)*

---

## 📁 Project Structure


