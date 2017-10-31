# Summary of approach

The submitted code './src/find_political_donors.py' aims in processing .txt file in input folder
with information that conform to the data dictionary described by the FEC. It will generate two
files. One output file keeps running median, number of donations and total amount of donations
for each recipient-zip code combination. The other output file keeps median, number of donations
and total amount of donations for each recipient-date combination.

  Major steps:
  1. Read file from the target folder
  2. Check validity of information and keep the core information from the valid entries
  3. Calculate running median, transaction number and total transaction for
     each recipient-zip code combination
  4. Calculate median, transaction number and total transaction for each recipient
     -date combination
  5. Convert the output information to correct format
  6. Save output to the target folder

  Highlight of approach:
  1. Dictionaries are used for keeping and retrieving information for each recipient-zip
     and recipient-date combination
  2. To ensure scalability, the current code combines min-max heap method as well as the
     counting sort algorithm to implement running median. For each recipient-zip combination,
     all the history transactions are stored in two heaps separated by the median. Instead of
     storing the absolute value, the location of the transaction in either below heap (0 ~ maximum
     value below/equal median) or above heap (minimum value below/equal median ~ maximum value)
     is marked by the number of occurrence of its specific amount. Therefore, for each new
     coming transaction, below heap and above heap are updated. Median could then be calculated
     using the maximum value in below heap and minimum value in the above heap.
  3. To ensure correct running of the code for unforeseen cases. Several test sets have been
     created, which test the correct calculation of the running median, the correct key generation
     for each recipient combination, the entry format of CMTE_ID, ZIP_CODE, DATE and Other_ID

# Dependencies
  The code should be run under the python 3 environment. os and path from the standard
  library are used. No extra library needs to be installed.

# Run instructions
   1. Make sure that the find_political_donors.py is under ./src folder
   2. In run.sh, the code format should be:
      python3 find_political_donors.py input-file-path-.txt output-file-path1-.txt output-file-path2-.txt
   3. The default input file name is 'itcont.txt' and default output names are 'medianvals_by_zip.txt'
      and 'medianvals_by_date.txt'.
   4. Put the .txt file that you would like to process in the input folder. Please update the
      input-file-path-.txt in run.sh with the .txt name in the input folder.
   5. Execute ./run.sh, two .txt files should be seen in your target output folders.
   6. To run the test code, execute ./run_tests.sh in the insight_testsuite folder. Five test cases
      have been given.
