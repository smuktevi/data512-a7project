# data512-a7project
DATA 512 Final Project: A4-7

## Goal
The goal of this assignment is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.

Follow the Python Notebook that can be found [here](https://github.com/smuktevi/data512hw/blob/main/data-512-a2/hcds-a2-bias.ipynb) to reproduce the same results of the analysis. Detailed steps on how the data was collected, transformed and visually analysed can be found in the same notebook.

## License and Sources

This repository uses the MIT license.  
  
This repository uses two data sources.

* The Wikipedia politicians by country dataset can be found on [Figshare](https://figshare.com/articles/dataset/Untitled_Item/5513449). Download and unzip it to extract the data file, which is called `page_data.csv`.

`Note:` In the case of page_data.csv, the dataset contains some page names that start with the string "Template:". These pages are not Wikipedia articles.

* The population data is available in CSV format as `WPDS_2020_data.csv`. This dataset is drawn from the world population data sheet published by the [Population Reference Bureau](https://www.prb.org/international/indicator/population/table/).

`Notes:` Similarly, `WPDS_2020_data.csv` contains some rows that provide cumulative regional population counts, rather than country-level counts. These rows are distinguished by having ALL CAPS values in the 'Geography' field (e.g. AFRICA, OCEANIA). These rows won't match the country values in `page_data.csv`, but you will want to retain them (either in the original file, or a separate file) so that you can report coverage and quality by region in the analysis section.

## Article Quality

Used a machine learning system called ORES to obtain article quality. The article quality estimates are, from best to worst:

FA - Featured article
GA - Good article
B - B-class article
C - C-class article
Start - Start-class article
Stub - Stub-class article

You can obtain these values by using ORES REST API endpoint. 

`Note:` 
* Review the [ORES REST documentation](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model). It expects a revision ID, which is the third column in the Wikipedia dataset, a model, which is "articlequality", and context which is "enwiki".  
* It's possible that you will be unable to get a score for a particular article. You can find the list of articles which did not retrieve scores in my case in `page_data_not_found.csv` and the ones that did get a score in `page_data_filtered_final.csv`.
* I used saved intermediate data after using the API as it takes a while to run the API call. The data can be found for both population and articles in `country_pop_data.csv` and `page_data_filtered_final.csv` respectively.

## Resulting Data