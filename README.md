## Explanation of Each Command

1. **Delete Command**:
   - `rm data/test-1`: This command removes the file named `test-1` located in the `data` directory.

2. **Move Command**:
   - `mv top-5-lowest-temparatures.csv analyzed/`: This command moves the specified CSV file from the root directory to the `analyzed` directory.

3. **Rename Command**:
   - The loop iterates over each file in the `analyzed` directory.
   - It checks if the item is a file and does not start with "top-5".
   - If it doesn't match, it renames the file by prefixing it with "top-5-".
i write this scipt in order to rename the file with "top-5-"
     
#!/bin/bash

for file in *; do
    if [ -f "$file" ]; then
        if [[ "$file" != top-5* ]]; then
            mv "$file" "top-5-$file"
        fi
    fi
done

TASK 2

# 
sort satelite_temperature_data.csv | uniq > temp_clean.csv
mv temp_clean.csv satelite_temperature_data.csv

#
sort -t, -k2,2nr satelite_temperature_data.csv | head -n 5 > analyzed/top-5-highest-temperatures.csv

# 
sort -t, -k2,2n satelite_temperature_data.csv | head -n 5 > analyzed/top-5-lowest-temperatures.csv

#
grep 'Rwanda' satelite_temperature_data.csv > analyzed/country-heat_data.csv

#
Gift worked on the  extraction of the top 5 highest recorded heat temperatures from the Months mentioned in the dataset.
cat satelite_temperature_data.csv | sort -t ',' -k3 -nr | head -5 > top-5-highest-temperatures.csv
