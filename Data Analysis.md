### Data Analysis
In this file, the given data will be anaylized before fitting. 

1- Stores Analysis

2- Training Dataframe Analysis

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
      
  After examining size distribution, the stats of stores and correlation of size with type will be discussed. In the following table, number of type stores, mean size, median size and standard deviation size of corresponding type. 
  ![](DA_imgs/stores_stats.png)
 
In the following bar-chart, y axis represents size of stores and x axis represents store id. Moreover, type of each store is marked with different colors (see pie-chart).
  ![](DA_imgs/stores_bar.png)
  
It can be concluded that while A type of stores are generally big sized stores, B type of stores are medium and C type of stores are small sized stores. 

#### Training Dataframe Analysis
In the following tables, merged dataframe and its statistics will be visualized.
![](DA_imgs/final_df.png)

For better resolution, please click on the table and examine the table in following tab.
![](DA_imgs/final_df_stats.png)

While there may be some information to extract, for better representation, correlation matrix will be visualized.
![](DA_imgs/corr_matrix.png)

and its thresholded version. For feature selection, I've used 0.25 value for thresholding the correlation. In other words, if two features are correlated more than abs(0.25), then they are correlated.
![](DA_imgs/th_corr_matrix.png)

The (negative) correlation can be seen in between CPI-Unemployment and (encoded)Type-Size. For better illustration, their average changes over date will be plotted. 

Average changes: the dataframe is groupby date and each group is averaged. In other words, below each feature, there is average value on given date. Main idea is to generalize the dataframe. New averaged dataframe looks like in below.
![](DA_imgs/average_df.png)

After explaining average dataframe, average dataframe's CPI changes and Unemployment changes over time is plotted, in the next two figures.

![](DA_imgs/average_CPIvsunemp.png)
![](DA_imgs/average_sizevstype.png)

In the plots, it is more obvious that each two features are negatively proportional to each other. It means that, using both of the features does not make huge difference at results than using only one of them. On the other hand, using more features will require more time to process during fitting. Thus, only one of each plots can be used for fitting.

In the next figures, the Weekly Sales changes and each feature's changes over date will be plotted and examined. 

1st graph: Weekly Sales and Temperature over Date
![](DA_imgs/average_temp.png)

2nd graph: Weekly Sales and CPI over Date
![](DA_imgs/average_CPI.png)

3rd graph: Weekly Sales and Fuel Price over Date
![](DA_imgs/average_fuel.png)

4th graph: Weekly Sales and Unemployment over Date
![](DA_imgs/average_unemp.png)

5th graph: Weekly Sales and Christmas over Date
![](DA_imgs/average_christ.png)

6th graph: Weekly Sales and Thanksgiving Day over Date
![](DA_imgs/average_thanks.png)

7th graph: Weekly Sales and Labor Day over Date
![](DA_imgs/average_labor.png)

8th graph: Weekly Sales and Super Bowl over Date
![](DA_imgs/average_super.png)

It is hard to give a comment for the first four graph. Hence feature_importance method of scikit-learn will be used for measuring their importance for fitting.

On the other hand, it can be easily said that during Thanksgiving Day and right before Christmas there are peaks at sales and high sales in between these days. Also, after Christmas there is dip and it lasts until Super Bowl. About Labor Day, there is a slight decrease at sales after the day.

To conclude, the last four features will surely help the model during fitting. The first four features should be analyzed  by feature importance method after initial fitting. 

Moreover, as aforementioned, due to the correlation values in between CPI-Unemployment and Type-Size, fitting can be performed only by including one feature of each pair.
