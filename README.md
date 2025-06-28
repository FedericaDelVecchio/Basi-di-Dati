# COVID-19 Database Management System (Italy)

A comprehensive database management system for tracking and analyzing COVID-19 data across Italian regions and provinces, built with Oracle SQL.

## 📋 Overview

This project implements a normalized relational database system to store, manage, and analyze COVID-19 statistics for Italy. The database covers data from February 2020 through May 2020, providing detailed insights into the pandemic's progression across different Italian administrative divisions.

## 🗂️ Project Structure

```
├── 1-TABELLA-MASTER-COVID.txt        # Master COVID table creation
├── 2-INSERT-DATI-PARTE-1.txt         # Data insertion (Part 1)
├── 3-INSERT-DATI-PARTE-2.txt         # Data insertion (Part 2)
├── 4-NORMALIZZAZIONE.txt              # Database normalization (3NF)
├── 5-ALTER-REGIONI.txt                # Regions table modifications
├── 6-ALTER-PROVINCE.txt               # Provinces table modifications
├── 7-ALTER-COVID_REGIONI-PARTE-1.txt # Regional COVID data updates (Part 1)
├── 8-ALTER-COVID_REGIONI-PARTE-2.txt # Regional COVID data updates (Part 2)
├── procedure, funzioni e trigger/     # Stored procedures, functions & triggers
│   ├── funzione7.txt
│   ├── funzione8.txt
│   ├── procedura1.txt
│   ├── procedura2.txt
│   ├── procedura3.txt
│   ├── procedura4.txt
│   ├── procedura5.txt
│   ├── procedura6.txt
│   ├── trigger1.txt
│   ├── trigger2.txt
│   ├── trigger3.txt
│   ├── trigger4.txt
│   └── trigger5.txt
├── query/                             # SQL queries for data analysis
│   ├── query1.txt
│   ├── query17.txt
│   └── ...
├── viste/                            # Database views
└── tesina.pdf                        # Project documentation (Italian)
```

## 🎯 Key Features

### Database Structure
- **Normalized to 3NF**: Eliminates data redundancy and ensures data integrity
- **Multi-table architecture**: Separate tables for regions, provinces, and COVID data
- **Referential integrity**: Foreign key constraints ensure data consistency

### Core Tables
- **REGIONI**: Italian regions with demographic and infrastructure data
- **PROVINCE**: Italian provinces with geographic and administrative information
- **COVID_REGIONI**: Daily COVID-19 statistics by region
- **COVID_PROVINCE**: Daily COVID-19 cases by province

### Advanced Database Features
- **Stored Procedures**: Automated data analysis and validation
- **Functions**: Custom calculations for COVID-19 metrics
- **Triggers**: Automatic data integrity checks and updates
- **Views**: Simplified data access for complex queries

## 📊 Data Coverage

### Time Period
- **Start Date**: February 26, 2020
- **End Date**: May 3, 2020
- **Frequency**: Daily updates

### Geographic Coverage
- **20 Italian Regions** (including autonomous provinces)
- **107+ Provinces**
- Complete demographic and infrastructure data

### COVID-19 Metrics
- Hospitalized patients with symptoms (`ricoverati_con_sintomi`)
- Intensive care patients (`terapia_intensiva`)
- Home isolation cases (`isolamento_domiciliare`)
- Total positive cases (`totale_positivi`)
- New daily cases (`nuovi_positivi`)
- Recovered patients (`dimessi_guariti`)
- Deaths (`deceduti`)
- Total cases (`casi_totali`)
- Tests performed (`tamponi`)

## 🛠️ Technical Implementation

### Database Management System
- **Oracle SQL**: Full compatibility with Oracle Database
- **ACID Compliance**: Ensures data reliability and consistency
- **Transaction Management**: Proper commit/rollback procedures

### Key Procedures & Functions
- **Population Monitoring**: Alert system for infection rates
- **ICU Capacity Alerts**: Warning system for hospital capacity
- **Data Validation**: Automatic integrity checks
- **Regional Analysis**: Statistical calculations and trend analysis

### Example Queries
- Regional comparison of positive test rates
- Hospital capacity utilization analysis
- Trend analysis across different time periods

## 🚀 Getting Started

### Prerequisites
- Oracle Database (11g or higher)
- SQL*Plus or compatible Oracle client
- Sufficient database privileges for DDL operations

### Installation
1. Execute scripts in numerical order:
   ```sql
   -- 1. Create master table
   @1-TABELLA-MASTER-COVID.txt
   
   -- 2. Insert initial data
   @2-INSERT-DATI-PARTE-1.txt
   @3-INSERT-DATI-PARTE-2.txt
   
   -- 3. Normalize database
   @4-NORMALIZZAZIONE.txt
   
   -- 4. Add demographic data
   @5-ALTER-REGIONI.txt
   @6-ALTER-PROVINCE.txt
   
   -- 5. Update COVID statistics
   @7-ALTER-COVID_REGIONI-PARTE-1.txt
   @8-ALTER-COVID_REGIONI-PARTE-2.txt
   ```

2. Install procedures, functions, and triggers:
   ```sql
   @procedure, funzioni e trigger/procedura1.txt
   @procedure, funzioni e trigger/trigger1.txt
   -- Continue with all files in the directory
   ```

## 📈 Usage Examples

### Query Regional Statistics
```sql
-- Get COVID statistics for a specific date
SELECT R.denominazione_regione, 
       C.totale_positivi, 
       C.nuovi_positivi,
       C.deceduti
FROM COVID_REGIONI C 
JOIN REGIONI R ON C.codice_regione = R.codice_regione
WHERE C.data = '05-Apr-2020'
ORDER BY C.totale_positivi DESC;
```

### Calculate Test Positivity Rate
```sql
-- Calculate percentage of positive tests by region
SELECT R.denominazione_regione,
       (C.casi_totali * 100.0 / C.tamponi) AS positivity_rate
FROM COVID_REGIONI C 
JOIN REGIONI R ON C.codice_regione = R.codice_regione
WHERE C.data = '05-Apr-2020' AND C.tamponi > 0
ORDER BY positivity_rate DESC;
```

## 🔧 Database Features

### Triggers
- **Region Code Updates**: Automatic propagation of region code changes
- **Auto-insertion**: Automatic creation of province and region records
- **Data Validation**: Population vs. infection rate validation

### Stored Procedures
- **Regional Analysis**: COVID statistics by region and date
- **Hospital Capacity**: ICU bed availability monitoring
- **Trend Analysis**: Day-over-day comparison of statistics

## 📚 Documentation

The complete project documentation is available in `tesina.pdf` (Italian).

## 🤝 Contributing

This project represents a complete database implementation for academic purposes. For improvements or extensions:

1. Fork the repository
2. Create a feature branch
3. Implement your changes
4. Test with sample data
5. Submit a pull request

## 📝 License

This project is developed for educational purposes. Please refer to the original data sources for usage rights of the COVID-19 statistics.

## 🙏 Acknowledgments

- Italian Civil Protection Department for COVID-19 data
- Regional and provincial administrative offices for demographic data
- Oracle Corporation for database technology

---

**Author**: Federica Del Vecchio  
**Institution**: Università degli Studi di Napoli "Federico II"  
**Year**: 2020