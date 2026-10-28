# Trademark–CRSP Matching Dataset

## About the dataset

This is a preliminary version of a trademark–CRSP matching dataset compiled by **Po-Hsuan Hsu** (National Tsing Hua University, <pohsuanhsu@mx.nthu.edu.tw>) and **Shihe Li** (Adelaide University, <shihe.li@adelaide.edu.au>).

The dataset links USPTO trademark records to publicly listed U.S. firms, with ownership tracked over time. The various dimensions and indicators that can be constructed from it speak to a wide range of questions, including firms' product development (new trademarks signalling new product lines), the composition of existing product lines (marks held across different classes), marketing strategy (full-spectrum versus niche positioning), product variety (multiple brands within the same product category), and the commercialization of inventions.

We hope you find it useful, and we welcome feedback.

## Data versions

The version released on 13 March 2026 is the first public release (trademark_owner_after_M&A_13032026.csv, 1,404,605 ownership periods).

The version released on 27 October 2026 is the latest data. 

## Current version (27 October 2026)

File: Trademark-CRSP_alpha.zip → trademark_owner_after_M&A_27102026.csv

| | |
| --- | --- |
| Ownership periods (rows) | 1,534,057 |
| Trademark serials | 1,278,424 |
| Public firms (lpermno) | 15,987 |
| Periods created by a recorded transfer (ma_buying = TRUE) | 218,528 |
| Periods still open at the end of coverage (owner_end_date = 2999-12-31) | 158,023 |
| Filing dates | 1884-06-16 to 2024-03-12 |

Each row is one (firm, trademark) ownership period. A trademark that changes hands between public firms appears once per owner; 206,784 serials have more than one row.

## Citation and acknowledgment

If you use this dataset in your research, please acknowledge **Po-Hsuan Hsu** and **Shihe Li** for sharing it. The dataset builds on and extends Po-Hsuan Hsu's earlier work on trademarks:

1. Hsu, P. H., Li, D., Li, Q., Teoh, S. H., & Tseng, K. (2022). Valuation of new trademarks. *Management Science*, 68(1), 257–279.
2. Hsu, P. H., Li, K., Liu, X., & Wu, H. (2022). Consolidating product lines via mergers and acquisitions: Evidence from the USPTO trademark data. *Journal of Financial and Quantitative Analysis*, 57(8), 2968–2992.
3. Hsu, P. H., & Li, S. (2026). Don't dress like me: The value implications of trade dress protection. *Working paper*.

## Coverage 

The dataset is built from the most recent releases of the USPTO Trademark Assignment and Trademark Case File datasets, both of which currently end in **early 2024**. The USPTO has not issued an update to either file since then, so trademark activity after that point is not observed.

## Files

- **Trademark-CRSP_alpha.zip** → trademark_owner_after_M&A_27102026.csv: trademark–firm ownership periods, 1884 to early 2024 (eight variables, one row per firm–trademark ownership period).
- **Online Appendix.pdf**: construction of the link table (name cleaning, matching, ownership periods from case files, assignment records and M&A deals, validation).

All dates are yyyy-mm-dd. ma_buying is the string TRUE or FALSE. The file is sorted by lpermno, serial_no, owner_start_date.

## Variable list

| Variable | Description |
| --- | --- |
| lpermno | CRSP permanent identifier of the owning firm (from the CRSP/Compustat Merged linking table). |
| serial_no | USPTO serial number; unique identifier for each trademark. |
| filing_dt | Filing date of the trademark application. |
| registration_dt | Registration date of the trademark. |
| owner_start_date | Date on which the mark became owned by this public firm. |
| owner_end_date | Date on which the firm's ownership of the mark ended. Set to 2999-12-31 for marks still held by the firm at the end of the coverage period. |
| end_date | Date on which the mark itself ceased to be in force. Set to 2999-12-31 for marks still live at the end of the coverage period. |
| ma_buying | TRUE if this ownership period begins with a recorded transfer of the mark to the firm (a USPTO assignment record or an SDC merger or acquisition); FALSE if the period comes from the USPTO owner record itself (the firm filed the mark or is listed as its owner). Ownership timing is captured by owner_start_date and owner_end_date. |

The dataset can be merged back to the underlying USPTO files, available at <https://data.uspto.gov/bulkdata>. We recommend the two academic releases: *Trademark Assignment Data for Academia and Researchers* and *Trademark Case File Data for Academia and Researchers*.

## Using the data

A firm lpermno holds trademark serial_no on date *t* if owner_start_date <= t <= owner_end_date and t <= end_date. New marks filed by the firm are the rows with ma_buying = FALSE and owner_start_date = filing_dt; marks acquired are the rows with ma_buying = TRUE.

Example (serial 73531782, also Table OA8 of the Online Appendix): filed by Zondervan (84145) in 1985, held by Twenty-First Century Fox (90441) from 2005, and transferred to Disney (26403) on 21 March 2019 through the Fox acquisition.

| lpermno | serial_no | filing_dt | registration_dt | owner_start_date | owner_end_date | end_date | ma_buying |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 84145 | 73531782 | 1985-04-12 | 1985-11-12 | 1985-04-12 | 1988-09-30 | 2999-12-31 | FALSE |
| 90441 | 73531782 | 1985-04-12 | 1985-11-12 | 2005-04-07 | 2019-03-20 | 2999-12-31 | FALSE |
| 26403 | 73531782 | 1985-04-12 | 1985-11-12 | 2019-03-21 | 2999-12-31 | 2999-12-31 | TRUE |

## Notes

1. A trademark that changes hands between public firms appears once per owner; 206,784 serials have more than one row. Each (serial_no, lpermno, owner_start_date) appears once.

2. For 21,385 serials (1.7%) two firms are recorded as owners from the same start date, because the USPTO assignment record and the SDC M&A record attribute one transfer to two CRSP identifiers (typically a parent and a listed subsidiary). We keep both rows rather than choose between them. Users who need a unique owner can keep the row whose lpermno matches the firm's own filings, or drop these serials.

3. registration_dt is missing for applications that were never registered (430,703 periods). filing_dt is missing for 8,451 periods and end_date for 2,984 periods; these marks are observed only in the assignment file, with no case-file record.

4. Ownership periods can start or end after the USPTO coverage end (latest owner_start_date 2025-08-15) when the period is cut by a CRSP/Compustat link date or an SDC deal date rather than by a USPTO record.

5. The public-firm universe is every PERMNO in the CRSP/Compustat Merged linking table; it is not restricted to common shares. Apply your own share-code or exchange screen after merging with CRSP.

6. Marks whose owner name maps to more than one public firm, and could not be resolved to one, are not assigned (see Online Appendix, Section V).

## Further reading

For details on the structure of the USPTO trademark data — classification, references, applications, publications, and so on — see:

1. Graham, S. J., Hancock, G., Marco, A. C., & Myers, A. F. (2013). The USPTO trademark case files dataset: Descriptions, lessons, and insights. *Journal of Economics & Management Strategy*, 22(4), 669–705.
2. Graham, S. J., Marco, A. C., & Myers, A. F. (2018). Monetizing marks: Insights from the USPTO trademark assignment dataset. *Journal of Economics & Management Strategy*, 27(3), 403–432.

## Contact

Questions about the dataset should be directed to **Po-Hsuan Hsu** (<pohsuanhsu@mx.nthu.edu.tw>).
