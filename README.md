# Stock2Vec

Stock prices are flutuated in every day. So, in each day, put those stocks in order of price change to one sentence. Then, with certain window size, each stock will show up with highly related stock frequently, because they tend to move their prices together.  
For example, [005380(Hyundai Motors)](http://finance.yahoo.com/quote/005380.KS/?p=005380.KS) moves together with [000270(Kia Motors)](http://finance.yahoo.com/quote/000270.KS/?p=000270.KS). Because not only they are in same industry, but also Hyndai owns Kia.

## Why it matters?
Every stock are related with others, but we couldn't represent it as a vector. With this result, we can get a similarity between stocks. Moreover, we can put those vectors to our classifier such as Deep Neural Network.

## In this repo
Embedding is done with Skip-gram from Word2Vec, and GloVe, but code for embedding is not included because there are already wide spreaded. 

You can figure out which stock is related with cosine similarity. In addition, some of result files are delimited with "\001" because I wanted to put those to Hive. Belows are short description about included files.

## File description
- sentences.txt: Source file. Each day has one row. Each row represent a set of stocks which is sorted by price difference between the day and a day before that day.
- sentences.refined.output.txt: There are 3 columns (source stock, dest stock, similarity based on **Skip-gram**) and they are "\001" delimited. 
- sentences.refined.output_glove.txt: There are 3 columns (source stock, dest stock, similarity based on **GloVe**) and they are "\001" delimited. 
- sentences.refined.vectors.txt: Columns are "\t" delimited. First column represents a stock code and rest are vectors from **Skip-gram**.
- sentences.refined.gloves.txt: Columns are "\t" delimited. First column represents a stock code and rest are vectors from **GloVe**.

## Sample of related stocks for [005380(Hyundai Motors)](http://finance.yahoo.com/quote/005380.KS/?p=005380.KS)

### skip-gram
| code | dest_code | similarity |
| --- | --- | --- |
| 005380 | [012330](http://finance.yahoo.com/quote/012330.KS) | 0.9679 |
| 005380 | [005387](http://finance.yahoo.com/quote/005387.KS) | 0.9677 |
| 005380 | [005385](http://finance.yahoo.com/quote/005385.KS) | 0.9491 |
| 005380 | [000270](http://finance.yahoo.com/quote/000270.KS) | 0.9306 |
| 005380 | [005389](http://finance.yahoo.com/quote/005389.KS) | 0.9176 |
| 005380 | [000240](http://finance.yahoo.com/quote/000240.KS) | 0.8904 |
| 005380 | [009155](http://finance.yahoo.com/quote/009155.KS) | 0.8859 |
| 005380 | [009150](http://finance.yahoo.com/quote/009150.KS) | 0.8849 |
| 005380 | [005850](http://finance.yahoo.com/quote/005850.KS) | 0.8805 |
| 005380 | [006405](http://finance.yahoo.com/quote/006405.KS) | 0.8723 |
| 005380 | [034220](http://finance.yahoo.com/quote/034220.KS) | 0.8704 |
| 005380 | [010690](http://finance.yahoo.com/quote/010690.KS) | 0.8679 |
| 005380 | [007860](http://finance.yahoo.com/quote/007860.KS) | 0.8672 |
| 005380 | [018880](http://finance.yahoo.com/quote/018880.KS) | 0.8667 |
| 005380 | [086280](http://finance.yahoo.com/quote/086280.KS) | 0.8654 |

### glove
| code | dest_code | similarity |
| --- | --- | --- |
| 005380 | [005387](http://finance.yahoo.com/quote/005387.KS) | 0.9273 |
| 005380 | [000270](http://finance.yahoo.com/quote/000270.KS) | 0.9233 |
| 005380 | [005385](http://finance.yahoo.com/quote/005385.KS) | 0.9218 |
| 005380 | [012330](http://finance.yahoo.com/quote/012330.KS) | 0.9100 |
| 005380 | [005389](http://finance.yahoo.com/quote/005389.KS) | 0.8879 |
| 005380 | [033530](http://finance.yahoo.com/quote/033530.KS) | 0.7575 |
| 005380 | [009150](http://finance.yahoo.com/quote/009150.KS) | 0.7364 |
| 005380 | [002350](http://finance.yahoo.com/quote/002350.KS) | 0.7042 |
| 005380 | [005850](http://finance.yahoo.com/quote/005850.KS) | 0.7012 |
| 005380 | [018880](http://finance.yahoo.com/quote/018880.KS) | 0.7001 |
| 005380 | [091180](http://finance.yahoo.com/quote/091180.KS) | 0.6935 |
| 005380 | [000240](http://finance.yahoo.com/quote/000240.KS) | 0.6934 |
| 005380 | [002550](http://finance.yahoo.com/quote/002550.KS) | 0.6719 |
| 005380 | [003620](http://finance.yahoo.com/quote/003620.KS) | 0.6705 |
| 005380 | [007860](http://finance.yahoo.com/quote/007860.KS) | 0.6686 | 
