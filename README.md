# picasso2025
this is the github space for the picasso code files to be stored and shared.

''' 
Required Files;
reu2025.ipynb
KDTW_1973Test - KDTW1973.csv
'''
the category of data I would like to access is the 'MW1' column, containing numbers with certain weather conditions observed at the time of recording.
there are multiple numbers that indicate observations of freezing rain ('25', '47', '48', '54', '55', '56', '64', '65', '66').
my goal is to firstly, gather all of the observations in the 'MW1' column, and then aggregate all of the times that those freezing rain occurrences appear.

ideally, i would like to know how many times all of these occurrences ring up, and a secondary goal would be to find if any freezing rain observations occur 3 times in a row.

'''
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import datetime as dt 

# Read the CSV file
datafile = pd.read_csv('KDTW_1973 - KDTW_1973.csv')
# Display the first few rows

#
report_types = datafile['REPORT_TYPE'].tolist
print(report_types)

saoreports = [report_types for report_types in datafile['REPORT_TYPE'] if report_types == 'SAO  ']
print(saoreports)
print(len(saoreports))

observations = datafile['MW1'].tolist
print(observations)

quality = datafile['MW1Q'].tolist
print(quality)

legitobservations = []


timestamp = datafile['DATE']

#make a count for the number of freezing rain hours below
#freezingrain = [observations for observations in datafile['MW1'] if observations == '25']
#print(freezingrain)

freezingrain = ['25', '47', '48', '54', '55', '56', '64', '65', '66']
freezingrain_counts = {target: saoreports.count(target) for target in freezingrain}

print(freezingrain_counts)


#counts = [freezingrain_counts[t] for t in freezingrain]

# plot some beautiful histograms and counts
#plt.figure(figsize=(10, 6))
#plt.bar(freezingrain, freezingrain_counts, color='skyblue', edgecolor='black')
plt.xlabel('MW1 Values')
plt.ylabel('Frequency')
plt.title('Frequency of Selected MW1 Values')
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.tight_layout()
'''

* code segment ends *
