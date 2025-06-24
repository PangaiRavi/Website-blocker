# Website-blocker
import time

# List of websites to block
websites_to_block = ["www.facebook.com", "facebook.com", "www.instagram.com", "instagram.com"]

# Path to the hosts file (Windows/Unix-based systems)
hosts_path = "/etc/hosts"  # For Linux/Mac
# hosts_path = r"C:\Windows\System32\drivers\etc\hosts"  # For Windows

# Redirect to the localhost (this makes the websites unreachable)
redirect = "127.0.0.1"

def block_websites():
    while True:
        # Open the hosts file
        with open(hosts_path, "r+") as file:
            content = file.read()
            for website in websites_to_block:
                # Check if the website is already blocked
                if website not in content:
                    # Block website by adding entry to the hosts file
                    file.write(f"\n{redirect} {website}")
                    print(f"Blocking {website}...")
        time.sleep(10)

def unblock_websites():
    with open(hosts_path, "r+") as file:
        content = file.readlines()
        file.seek(0)
        for line in content:
            # Remove the lines that contain the website to unblock
            if not any(website in line for website in websites_to_block):
                file.write(line)
        file.truncate()

# Block websites for 60 seconds
block_websites()

# Uncomment to unblock after testing
# unblock_websites()
