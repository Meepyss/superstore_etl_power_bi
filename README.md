
# **Origem dos dados/Dataset:**
 https://www.kaggle.com/datasets/vivek468/superstore-dataset-final
 
# superstore_etl_power_bi
Um projeto de análise de dados de uma empresa fícticia(DADOS KAGGLE) utilizando Python e PowerBI 

# Global Superstore BI Project

## Visão Geral
Este repositório contém o projeto completo de Business Intelligence aplicado ao dataset **Global Superstore**. Nele você encontrará:  
- **ETL em Python**: carregamento, limpeza, transformação e criação de um star schema (dimensões e tabela de fatos).  
- **Power BI Dashboard**: modelo dimensional importado e dashboards interativos com KPIs, gráficos de tendência, análises geográficas e filtros dinâmicos.  

O objetivo é demonstrar todo o fluxo de trabalho — desde a obtenção dos dados até a apresentação final — para recrutadores e estudantes.

## Tecnologias Utilizadas
- **Python 3.x** com pacotes: `pandas`
- **Power BI Desktop** (versão mais recente)  
- **DAX** para criação de medidas (Total Sales, Profit Margin, etc.)


## Estrutura do Repositório
```
├── data/                       # Dados brutos e limpos em CSV
│   ├── Sample - Superstore.csv   # CSV original do Kaggle
│   └── superstore_cleaned.csv  # CSV após ETL
│   └── dim_data.csv
│   └── dim_produto.csv
│   └── dim_cliente.csv
│   └── dim_shipmode.csv
│   └── fact_vendas.csv
├── scripts/                    # Scripts de processamento
│   └── superstore_etl.py       # ETL e criação do star schema
├── powerbi/                    # Arquivos do Power BI
│   └── dashboard.pbix          # Modelo e dashboards prontos
│   └── screenshots/            # Imagens demonstrativas do dashboard
├── README.md                   # Documentação do projeto (este arquivo)
└── LICENSE                     # Licença do repositório
```

## Como Executar o ETL
1. Clone este repositório:  
   ```bash
   git clone https://github.com/seu-usuario/global-superstore-bi.git
   cd global-superstore-bi
   ```
2. Instale as dependências:  
   ```bash
   pip install pandas numpy
   ```
3. Coloque o arquivo `Global Superstore.csv` em `data/`.  
4. Execute o script de ETL:  
   ```bash
   python scripts/superstore_etl.py
   ```
   Isso gerará os CSVs das dimensões e da tabela de fatos em `data/`.

## Modelo Dimensional (Star Schema)
- **DimData**: atributos temporais (Year, Month, Quarter, DayOfWeek)  
- **DimProduto**: Category, Sub-Category, ProductName  
- **DimCliente**: Segment, Country, State, City, Region  
- **DimShipMode**: ShipMode  
- **FactVendas**: chaves para dimensões e medidas (Sales, Profit, Quantity, AvgOrderValue, DeliveryDays)

## Dashboard em Power BI
1. Abra o Power BI Desktop.  
2. Em **Get Data → CSV**, importe os arquivos `dim_*.csv` e `fact_vendas.csv` de `data/`.  
3. No **Model view**, crie relacionamentos 1:* entre a tabela de fatos e cada dimensão usando as chaves surrogate.  
4. Crie medidas DAX em **FactVendas**:  
   - `Total Sales = SUM('fact_vendas'[Sales])`  
   - `Profit Margin = DIVIDE(SUM('fact_vendas'[Profit]), SUM('fact_vendas'[Sales]), 0)`  
   - `Avg Order Value = AVERAGE('fact_vendas'[AvgOrderValue])`  
   - `Avg Delivery Days = AVERAGE('fact_vendas'[DeliveryDays])`  
5. Monte seus visuais (Cards, Line chart, Bar chart, Map, Slicers).  

## Demonstração e Publicação
- **Power BI Service**: publique o arquivo `.pbix` em seu workspace para gerar link público.  
- **Issue Tracker**: registre feedback ou dúvidas neste repositório.  

## Contribuição
Contribuições são bem-vindas! Abra um **Pull Request** ou **Issue** para sugestões de melhoria.

## Licença
Este projeto está licenciado sob a [MIT License](LICENSE).

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# Global Superstore BI Project

## Overview
This repository contains a complete Business Intelligence project applied to the **Global Superstore** dataset. It demonstrates the entire workflow—from data acquisition to final dashboard—so you can showcase your skills to recruiters and stakeholders.

### What’s Included
- **ETL in Python**: data loading, cleaning, transformation, and star schema creation (dimensions & fact table).  
- **Power BI Dashboard**: imported dimensional model and interactive visuals with KPIs, trend analysis, geographic insights, and dynamic filters.

## Technologies Used
- **Python 3.x** with `pandas`, `numpy`  
- **Power BI Desktop** (latest version)  
- **DAX** for measure creation (Total Sales, Profit Margin, etc.)

## Repository Structure
```
├── data/                       # Raw and processed CSV files
│   ├── Sample - Superstore.csv   # Original dataset from Kaggle
│   ├── superstore_cleaned.csv  # Cleaned dataset after ETL
│   ├── dim_data.csv            # Date dimension
│   ├── dim_produto.csv         # Product dimension
│   ├── dim_cliente.csv         # Customer dimension
│   ├── dim_shipmode.csv        # Ship mode dimension
│   └── fact_vendas.csv         # Fact table with measures & foreign keys
├── scripts/                    # Python scripts for ETL and modeling
│   └── superstore_etl.py       # ETL script that builds the star schema
├── powerbi/                    # Power BI assets
│   ├── dashboard.pbix          # Power BI report file
│   └── screenshots/            # Dashboard screenshots
├── README.md                   # Project documentation (this file)
└── LICENSE                     # MIT License
```

## Getting Started
1. **Clone the repo**:  
   ```bash
   git clone https://github.com/your-username/global-superstore-bi.git
   cd global-superstore-bi
   ```
2. **Install dependencies**:  
   ```bash
   pip install pandas numpy
   ```
3. **Place the original CSV**: download `Global Superstore.csv` from Kaggle and save it in the `data/` folder.  
4. **Run the ETL**:  
   ```bash
   python scripts/superstore_etl.py
   ```
   This generates all the dimension and fact table CSVs in `data/`.

## Dimensional Model (Star Schema)
- **DimData**: Year, Month, Quarter, DayOfWeek  
- **DimProduto**: Category, Sub-Category, ProductName  
- **DimCliente**: Segment, Country, State, City, Region  
- **DimShipMode**: ShipMode  
- **FactVendas**: DateID, ProductID, CustomerID, ShipModeID + Sales, Profit, Quantity, AvgOrderValue, DeliveryDays

## Power BI Dashboard
1. **Open** Power BI Desktop.  
2. **Get Data → CSV**: import `dim_data.csv`, `dim_produto.csv`, `dim_cliente.csv`, `dim_shipmode.csv`, and `fact_vendas.csv` from `data/`.  
3. **Model view**: create one-to-many relationships between **FactVendas** and each dimension using the surrogate keys.  
4. **Create DAX measures** under **FactVendas**:  
   ```DAX
   Total Sales = SUM('fact_vendas'[Sales])  
   Profit Margin = DIVIDE(SUM('fact_vendas'[Profit]), SUM('fact_vendas'[Sales]), 0)  
   Avg Order Value = AVERAGE('fact_vendas'[AvgOrderValue])  
   Avg Delivery Days = AVERAGE('fact_vendas'[DeliveryDays])
   ```
5. **Build visuals**: Cards, Line charts, Bar charts, Maps, and Slicers for interactive filtering.

## Publishing & Sharing
- **Export**: save your `.pbix` file and upload it to **Power BI Service** for a public share link.  
- **GitHub Pages**: optionally host project documentation or screenshots via GitHub Pages.  
- **LinkedIn & Resume**: share a post summarizing the project with a link to this repo and the live dashboard URL.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for improvements.

## License
This project is licensed under the MIT License.  



