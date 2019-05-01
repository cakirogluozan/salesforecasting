### Data Analysis
In this file, 

#### Stores Analysis
In the stores.csv file, there are several information columns for each store in Retail Stores. stores.csv dataframe can be shown as below.

![](imgs/stores_csv.png)

Every store has its type (A-B-C) and its size. In the following pie-chart, number of different types of stores are visualized.

![](DA_imgs/stores_pie.png)

As it can be seen, there are 22 A-type stores, 17 B-type stores and 6 C-type stores. In the next figure, distribution of sizes is visualized. It can be interpreted that stores can be classified by their size according to the size distribution of the stores. 

![](DA_imgs/stores_hist.png)

    if 0 <store.size < 75k:
        store = small
    elif 75k < store.size < 175k:
        store = medium
    elif 175k < store.size:
        store = big
    else:
        print('error value')
        return False
