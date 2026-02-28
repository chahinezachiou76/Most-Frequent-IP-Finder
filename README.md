# Solution
Extract the most frequent IP and save it to a file:

awk '{print $1}' /home/admin/access.log | sort | uniq -c | sort -nr | head -n 1 | awk '{print $2}' > /home/admin/highestip.txt

# How It Works
awk '{print $1}' → Extract the first column (IP address)  
sort → Sort IPs so duplicates are grouped together  
uniq -c → Count occurrences  
sort -nr → Sort by frequency  
head -n 1 → Select the top IP  
awk '{print $2}' → Extract only the IP  
> → Save to a file

# Verification
grep -c -F -f /home/admin/highestip.txt /home/admin/access.log
Expected output: 482

# Optional SHA1 Check
sha1sum /home/admin/highestip.txt
Expected: 6ef426c40652babc0d081d438b9f353709008e93

# Skills Learned
- Bash scripting  
- Log analysis  
- Command-line text processing  
- Pipelines
