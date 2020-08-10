# Election_Analysis

## Project Overview
This project pulls data from an election audit of a recent local congressional election. The purpose of this project is to create a python script that will readout the following info when executed: 
1. Total number of votes cast
2. A complete list of candidates who received votes
3. Total number of votes each candidate received
4. Percentage of votes each candidate won
5. The winner of the election based on popular vote

---
## Election Audit Results 
From the generated python script (under PyPoll_ChallengeFinal.py) the following readout was obtained: 
![alt text](https://github.com/NassimNatA/Election_Analysis/blob/master/Terminal_Screenshot.png)

---

* Per above, it can be seen that a total of 369.711 votes were cast. This was obtained by creating a for loop below: 

        with open(file_to_load) as election_data:
        reader = csv.reader(election_data)
        header = next(reader)
        for row in reader:
        total_votes = total_votes + 1
        candidate_name = row[2]
        county_names = row [1]

Then printing to the election_analysis.txt file: 

        election_results = (f"\nElection Results\n"
                f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")
    
---

* A breakdown of the number of votes and the percentage of total votes for each county in the precinct shows that Denver county had the largest number of votes:

1.Jefferson county had a total of 38, 855 votes. 

2.Denver county had a total of 305,055 votes. 

3.Araphone county had a total of 24,801 votes. 

This readout was obtained by the following code: 

        for county_names in county_votes_dict:
        cvotes = county_votes_dict[county_names]
        c_v_percentage = float(cvotes) / float(total_votes) * 100
        county_results = (
            f"{county_names}: {c_v_percentage:.1f}% ({cvotes:,})\n")
Then printing the code to the terminal: 

        print(county_results)
 
---

* A breakdown of the number of votes and the percentage of the total votes for each candidate show that DeGette had the largest number of votes with a total of 272,892 (74.8%):

1.Stockham: (85,213) 23.0$

2.DeGette: (272,892) 73.8%

3.Doan: (11,606) 3.1%

This readout was obtained by the following code: 

        for candidate_name in candidate_votes:
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
    f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")
Then printing the code to the terminal: 

        print(candidate_results)

---
* An observation from this script is that Denver is not in the terminal readout as the county with the highest number of votes, further debugging is required to utilize this script for complete accuracy.
---

## Election-Audit Summary

As shown above, this script breaks down the election data to produce a comprehensive summary of the election results. This script can be further used for any election outside of the provided election data from this Module. For example, the framework for: tracking a winning candidate, retriving vote count and percentage, determining winning vote count/winning percentage/and candidate can be retained while modifying two things in the script to make it more versatile: 

1. Retrieve state_vote instead of county_vote to apply this script to state-wide elections. 

2. For the candidate winner, determine how many votes they won by adding percent difference calculation after determining  winning vote count, winning percentage, and candidate.
