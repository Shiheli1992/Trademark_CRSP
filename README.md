# About the dataset
This dataset is the very preliminary version of the trademark-CRSP matching done by Po-Hsuan Hsu (National Tsing Hua U.: pohsuanhsu@mx.nthu.edu.tw) and Shihe Li (Adelaide University: shihe.li@adelaide.edu.au)

We hope that you will be able to get the most out of this dataset. All different dimensions and associated indicators based on USTPO trademark datasets can be used to capture firms’ product development (new trademarks for new product lines), product lines (existing trademarks of different classes), marketing strategies (full spectrum or only niche market), varieties (different brands of the same product), commercialization of inventions, etc. 

**If you use this dataset for your research, please acknowledge _Po-Hsuan Hsu_ and _Shihe Li_ for sharing the dataset, which is based on and extends Po’s earlier work in trademarks:**
1. Hsu, P. H., Li, D., Li, Q., Teoh, S. H., & Tseng, K. (2022). Valuation of new trademarks. Management Science, 68(1), 257-279.
2. Hsu, P. H., Li, K., Liu, X., & Wu, H. (2022). Consolidating product lines via mergers and acquisitions: Evidence from the USPTO trademark data. Journal of Financial and Quantitative Analysis, 57(8), 2968-2992.

If you have any question in this dataset, please contact Po. We will gather all issues and fix them in the next version.

## Variable list
1. lpermno: you know what it is
2. serial_no: unique serial number for each trademark 
3. filing_dt: the filing date of a trademark
4. registration_dt: the registration date of a trademark
5. owner_start_date: the starting date of this mark belong to this public firm
6. owner_end_date: the ending date of this mark belong to this public firm (for those of continued use as of 2024 end, we set the ending date to be 2999-12-31)
7. end_date the ending date of this mark (for those of continued use as of 2024 end, we set the ending date to be 2999-12-31)
8. ma_buying: whether there is any M&A involved in this mark (the ownership has been tracked in the owner_start_date and owner_end_date)

You can merge this dataset with USPTO trademark data via this link: https://data.uspto.gov/bulkdata (I recommend “Trademark Assignment Data for Academia and Researchers” and “Trademark Case File Data for Academia and Researchers”) 

## Further reading 
For more details of USPTO trademarks (such as classification, references, applications, publications, etc.), you are referred to these two papers:
1. Graham, S. J., Hancock, G., Marco, A. C., & Myers, A. F. (2013). The USPTO trademark case files dataset: Descriptions, lessons, and insights. Journal of Economics & Management Strategy, 22(4), 669-705.
2. Graham, S. J., Marco, A. C., & Myers, A. F. (2018). Monetizing marks: Insights from the USPTO trademark assignment dataset. Journal of Economics & Management Strategy, 27(3), 403-432.
