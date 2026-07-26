# Trademark–CRSP Matching Dataset

## About the dataset

This is a preliminary version of a trademark–CRSP matching dataset compiled by **Po-Hsuan Hsu** (National Tsing Hua University, <pohsuanhsu@mx.nthu.edu.tw>) and **Shihe Li** (Adelaide University, <shihe.li@adelaide.edu.au>).

The dataset links USPTO trademark records to publicly listed U.S. firms, with ownership tracked over time. The various dimensions and indicators that can be constructed from it speak to a wide range of questions, including firms' product development (new trademarks signalling new product lines), the composition of existing product lines (marks held across different classes), marketing strategy (full-spectrum versus niche positioning), product variety (multiple brands within the same product category), and the commercialization of inventions.

We hope you find it useful, and we welcome feedback.

## Citation and acknowledgment

If you use this dataset in your research, please acknowledge **Po-Hsuan Hsu** and **Shihe Li** for sharing it. The dataset builds on and extends Po-Hsuan Hsu's earlier work on trademarks:

1. Hsu, P. H., Li, D., Li, Q., Teoh, S. H., & Tseng, K. (2022). Valuation of new trademarks. *Management Science*, 68(1), 257–279.
2. Hsu, P. H., Li, K., Liu, X., & Wu, H. (2022). Consolidating product lines via mergers and acquisitions: Evidence from the USPTO trademark data. *Journal of Financial and Quantitative Analysis*, 57(8), 2968–2992.
3. Hsu, P. H., & Li, S. (2026). Don't dress like me: The value implications of trade dress protection. *Working paper*.

## Coverage and known limitations

The dataset is built from the most recent releases of the USPTO **Trademark Assignment** and **Trademark Case File** datasets, both of which currently end in early 2024. The USPTO has not issued an update to either file since then, so trademark activity after that point is not observed.

Two implications for users:

- **Right-censoring.** Ownership spells and mark statuses are only observed up to the end of the source data. Marks still in force at that point are coded with an end date of `2999-12-31` rather than a true termination date.
- **Preliminary status.** This version has not been fully validated. Please report any issues you encounter to Po-Hsuan Hsu; we will collect them and address them in the next release.

## Variable list

| Variable | Description |
| --- | --- |
| `lpermno` | CRSP permanent identifier of the owning firm (from the CRSP/Compustat Merged linking table). |
| `serial_no` | USPTO serial number; unique identifier for each trademark. |
| `filing_dt` | Filing date of the trademark application. |
| `registration_dt` | Registration date of the trademark. |
| `owner_start_date` | Date on which the mark became owned by this public firm. |
| `owner_end_date` | Date on which the firm's ownership of the mark ended. Set to `2999-12-31` for marks still held by the firm at the end of the coverage period. |
| `end_date` | Date on which the mark itself ceased to be in force. Set to `2999-12-31` for marks still live at the end of the coverage period. |
| `ma_buying` | Indicator for whether the ownership change involved an M&A transaction. Ownership timing is captured by `owner_start_date` and `owner_end_date`. |

The dataset can be merged back to the underlying USPTO files, available at <https://data.uspto.gov/bulkdata>. We recommend the two academic releases: *Trademark Assignment Data for Academia and Researchers* and *Trademark Case File Data for Academia and Researchers*.

## Further reading

For details on the structure of the USPTO trademark data — classification, references, applications, publications, and so on — see:

1. Graham, S. J., Hancock, G., Marco, A. C., & Myers, A. F. (2013). The USPTO trademark case files dataset: Descriptions, lessons, and insights. *Journal of Economics & Management Strategy*, 22(4), 669–705.
2. Graham, S. J., Marco, A. C., & Myers, A. F. (2018). Monetizing marks: Insights from the USPTO trademark assignment dataset. *Journal of Economics & Management Strategy*, 27(3), 403–432.

## Contact

Questions about the dataset should be directed to **Po-Hsuan Hsu** (<pohsuanhsu@mx.nthu.edu.tw>).
