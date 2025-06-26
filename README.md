\documentclass[a4paper,12pt]{article}
\usepackage{hyperref}
\usepackage{longtable}
\usepackage{geometry}
\geometry{margin=1in}

\title{CustomerDataExtractor Documentation}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle

\section*{Overview}

\texttt{CustomerDataExtractor} is a Python class designed to load, clean, and transform nested customer order data into a clean, flat \texttt{pandas.DataFrame} suitable for analysis. It robustly handles real-world data inconsistencies and integrates VIP customer information for enriched insights.

\section*{Features}

\begin{itemize}
    \item Loads customer order data from a pickled binary file.
    \item Loads VIP customer IDs from a text file.
    \item Cleans and standardizes prices, quantities, categories, and order IDs.
    \item Resolves product categories using a predefined mapping with fallback.
    \item Transforms nested customer and order data into a flat DataFrame.
    \item Calculates total item prices and their share of the total order value.
    \item Handles missing and malformed data robustly.
\end{itemize}

\section*{Requirements}

\begin{itemize}
    \item Python 3.7+
    \item \texttt{pandas}
    \item \texttt{numpy}
\end{itemize}

Dependencies can be installed using pip:

\begin{verbatim}
pip install pandas numpy
\end{verbatim}

\section*{Usage}

Prepare your data files:

\begin{itemize}
    \item \texttt{customer\_orders.pkl} -- Pickled list of customer records with nested orders and items.
    \item \texttt{vip\_customers.txt} -- Text file listing VIP customer IDs, one per line.
\end{itemize}

Example usage:

\begin{verbatim}
from customer_data_extractor import CustomerDataExtractor

extractor = CustomerDataExtractor(orders='customer_orders.pkl', vip='vip_customers.txt')
df = extractor.run()

print(df.head())
\end{verbatim}

\section*{Output DataFrame Columns}

\begin{longtable}{p{5cm} p{4cm} p{6cm}}
\hline
\textbf{Column} & \textbf{Type} & \textbf{Description} \\
\hline
customer\_id & int & Unique customer identifier \\
customer\_name & str & Customer's name \\
registration\_date & datetime64[ns] & Customer registration date \\
is\_vip & bool & True if customer is VIP, else False \\
order\_id & int & Unique order identifier \\
order\_date & datetime64[ns] & Date of the order \\
product\_id & int & Unique product/item identifier \\
product\_name & str & Name of the product \\
category & str & Product category (Electronics, Apparel, Books, Home Goods, or Misc) \\
unit\_price & float & Price per unit of the product \\
item\_quantity & int & Quantity ordered \\
total\_item\_price & float & Unit price multiplied by quantity \\
total\_order\_value\_percentage & float & Item's share of total order value \\
\hline
\end{longtable}

\section*{Category Mapping}

\begin{tabular}{ll}
\hline
Category ID & Category Name \\
\hline
1 & Electronics \\
2 & Apparel \\
3 & Books \\
4 & Home Goods \\
Others & Misc \\
\hline
\end{tabular}

\section*{Data Cleaning and Error Handling}

\begin{itemize}
    \item Invalid or missing prices are converted t
