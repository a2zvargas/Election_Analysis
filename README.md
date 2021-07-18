# Election_Analysis

## Overview of Election Audit: 
The purpose of this election audit analysis is to determine the winner of a US Congressional precinct in Colorado.  I intend to do this by using Python code to tabulate the votes that were provided in a CSV file and collected from mail-in ballots, punch cards, and direct recording electronic (DRE).

## Election-Audit Results: 

* Number of votes cast in this congressional election: 369,711

* Number of votes cast and percentage of votes by county:
  * Jefferson: 10.5% (38,855)
  * Denver: 82.8% (306,055)
  * Arapahoe: 6.7% (24,801)
   
* Largest County Turnout: Denver

* Number of votes cast and percentage for each candidate:
  * Charles Casper Stockham: 23.0% (85,213)
  * Diana DeGette: 73.8% (272,892)
  * Raymon Anthony Doane: 3.1% (11,606)

* Election Winner: Diana DeGette
  * Winning Vote Count: 272,892
  * Winning Percentage: 73.8%

Command Line Output of Python Code
:-------------------------:
![election_results](https://user-images.githubusercontent.com/85706721/126080344-cf284302-fad9-4705-a88f-cb1bb555ab35.png)


## Election-Audit Summary: 
To the Election Commission of the state of Colorado, I submit to you a business proposal in which this script (with some minor modifications) can be used for any election, such as Senatorial elections or local elections.

Below we have a snippet of code in the script used to tabulate the results by county for this Congressional election.  Next to it are examples of how the script can be changed to tabulate results by Senatorial districts for Senatorial elections, and by zip code for smaller local elections.

### By County 
```python
# 6a: Write a for loop to get the county from the county dictionary.
    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        votesByCounty = county_votes.get(county_name)
        # 6c: Calculate the percentage of votes for the county.
        votesPercentByCounty = float(votesByCounty) / float(total_votes) * 100
         # 6d: Print the county results to the terminal.
        county_results = (
            f"{county_name}: {votesPercentByCounty:.1f}% ({votesByCounty:,})\n")
        print(county_results)
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
         # 6f: Write an if statement to determine the winning county and get its vote count.
        if (votesByCounty > largest_county_count) and (votesPercentByCounty > largest_county_percentage):
            largest_county_count = votesByCounty
            largest_county = county_name
            largest_county_percentage = votesPercentByCounty
```

### By Senatorial District
```python
for district_name in district_votes:
        # 6b: Retrieve the district vote count.
        votesBydistrict = district_votes.get(district_name)
        # 6c: Calculate the percentage of votes for the district.
        votesPercentBydistrict = float(votesBydistrict) / float(total_votes) * 100
         # 6d: Print the district results to the terminal.
        district_results = (
            f"{district_name}: {votesPercentBydistrict:.1f}% ({votesBydistrict:,})\n")
        print(district_results)
         # 6e: Save the district votes to a text file.
        txt_file.write(district_results)
         # 6f: Write an if statement to determine the winning district and get its vote count.
        if (votesBydistrict > largest_district_count) and (votesPercentBydistrict > largest_district_percentage):
            largest_district_count = votesBydistrict
            largest_district = district_name
            largest_district_percentage = votesPercentBydistrict
```



### By Zip Code
```python
 # 6a: Write a for loop to get the zipcode from the zipcode dictionary.
    for zipcode_name in zipcode_votes:
        # 6b: Retrieve the zipcode vote count.
        votesByzipcode = zipcode_votes.get(zipcode_name)
        # 6c: Calculate the percentage of votes for the zipcode.
        votesPercentByzipcode = float(votesByzipcode) / float(total_votes) * 100
         # 6d: Print the zipcode results to the terminal.
        zipcode_results = (
            f"{zipcode_name}: {votesPercentByzipcode:.1f}% ({votesByzipcode:,})\n")
        print(zipcode_results)
         # 6e: Save the zipcode votes to a text file.
        txt_file.write(zipcode_results)
         # 6f: Write an if statement to determine the winning zipcode and get its vote count.
        if (votesByzipcode > largest_zipcode_count) and (votesPercentByzipcode > largest_zipcode_percentage):
            largest_zipcode_count = votesByzipcode
            largest_zipcode = zipcode_name
            largest_zipcode_percentage = votesPercentByzipcode
```

This script is very versatile and can be easily adapted for various types of elections.  The votes will be tabulated quickly and accurately, with the results presented in an easy to read format.
