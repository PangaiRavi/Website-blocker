# Website-Blocker
import time
from datetime import datetime as dt

# Path to the hosts file (adjust for Windows/Mac/Linux)
hosts_path = "/etc/hosts"  # Linux/Mac
# hosts_path = r"C:\Windows\System32\drivers\etc\hosts"  # Windows

redirect = "127.0.0.1"
websites_to_block = [
    "www.facebook.com",
    "facebook.com",
    
]

# Define blocking hours (e.g., 9 AM to 5 PM)
block_start = 9  # 9 AM
block_end = 17  # 5 PM

while True:
    current_hour = dt.now().hour

    if block_start <= current_hour < block_end:
        print("Work hours... Blocking sites")
        with open(hosts_path, "r+") as file:
            content = file.read()
            for website in websites_to_block:
                if website not in content:
                    file.write(f"{redirect} {website}\n")
    else:
        print("Outside work hours... Unblocking sites")
        with open(hosts_path, "r+") as file:
            content = file.readlines()
            file.seek(0)
            for line in content:
                if not any(website in line for website in websites_to_block):
                    file.write(line)
            file.truncate()
    
    time.sleep(300)  # Sleep for 5 minutes# Website-Blocker
import time
from datetime import datetime as dt

# Path to the hosts file (adjust for Windows/Mac/Linux)
hosts_path = "/etc/hosts"  # Linux/Mac
# hosts_path = r"C:\Windows\System32\drivers\etc\hosts"  # Windows

redirect = "127.0.0.1"
websites_to_block = [
    "www.facebook.com",
    "facebook.com",
    
]

# Define blocking hours (e.g., 9 AM to 5 PM)
block_start = 9  # 9 AM
block_end = 17  # 5 PM

while True:
    current_hour = dt.now().hour

    if block_start <= current_hour < block_end:
        print("Work hours... Blocking sites")
        with open(hosts_path, "r+") as file:
            content = file.read()
            for website in websites_to_block:
                if website not in content:
                    file.write(f"{redirect} {website}\n")
    else:
        print("Outside work hours... Unblocking sites")
        
 time.sleep(300)  # Sleep for 5 minutes
