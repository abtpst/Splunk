# Splunk
Splunk project done during RBC CMIT Splunk Hackathon.

In this project, we took a list of securities and compared their House price with the Bloomberg price. The intention was to identify any variance. If the house prices vary too much from the bloomberg price, then that is something which must be addressed. For our analysis, we looked at a month's worth of pricing data.

The project involved four major steps

1. Ingesting data into Splunk and creating a hierarchical directory structure with different indices.

We divided our data on the basis of geographical information. For instance all of the North American securities had a separate directory. Also, we created different indices for each type of security within a geographical region. So for example all of the Converts in the North American region went into the same index. This was needed as the files for each region and each security had a particular structure or order of columns. 

2. Filed extraction.

The files ingested in the previous step were pipe delimited, but did not have column headings. So we had to define our own fields. This was done using regular expressions. As can be seen here https://github.com/abtpst/Splunk/blob/master/fields.txt

3. Search queries in an interactive dashboard.

Once all the fields were extracted, we initially created two separate interactive dashboard's. One for Bloomberg prices lookup and one for House prices lookup. The source code, which includes the search queries, for both of these dashboards can be found at

https://github.com/abtpst/Splunk/blob/master/bbgQuery.txt

https://github.com/abtpst/Splunk/blob/master/houseQuery.txt

The House prices lookup is particularly interesting as it performs a join of two searches in order to create a price comparison table.

Both of these dashboards can take multiple Cusips as input. The Bloomberg dashboard has an ISIN input field which is a dynamically populated dropdown which uses a subquery behind the scenes.

4. Combined dashboard and Variance Plot.

The final step involved combining the two dashboards created in step 4 and plot the variance graph. The source code for the plot uses the same query as the House prices lookup, but additionally plots the results against the last updated date. The source code for this dashboard can be found at

https://github.com/abtpst/Splunk/blob/master/hackathon.txt

Note that all of the screenshots have been combined into a single pdf 

https://github.com/abtpst/Splunk/blob/master/splunkHack.pdf

My apologies but i had to cover up the actual data in the dashboard due to the firm's privacy policy. However, one can clearly make out the format of the reports and the columns that we extracted.

