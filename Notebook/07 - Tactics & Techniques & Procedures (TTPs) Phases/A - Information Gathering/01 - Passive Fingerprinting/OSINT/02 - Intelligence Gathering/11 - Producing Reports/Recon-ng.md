# Recon-ng

- `reporting/list` recon-ng module

```
[recon-ng][default] > marketplace install reporting/*

[recon-ng][default] > modules load reporting/list

[recon-ng][default][list] > options list

  Name      Current Value                                     Required  Description
  --------  -------------                                     --------  -----------
  COLUMN    ip_address                                        yes       source column of data for the list
  FILENAME  /home/user/.recon-ng/workspaces/default/list.txt  yes       path and filename for output
  NULLS     False                                             yes       include NULLs in the dataset
  TABLE     hosts                                             yes       source table of data for the list
  UNIQUE    True                                              yes       only return unique items from the dataset

[recon-ng][default][list] > options set COLUMN <column_1>,<column_2>,<column_n>

[recon-ng][default][list] > options set FILENAME /home/user/output.txt

[recon-ng][default][list] > run
```