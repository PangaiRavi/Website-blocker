blocked_websites = ["www.facebook.com", "www.youtube.com", "www.instagram.com"]

def is_website_blocked(website):
    return website.lower() in [w.lower() for w in blocked_websites]

def main():
    print("Website Blocker Simulator")
    website = input("Enter the website URL to visit (e.g., www.google.com): ").strip()

    if is_website_blocked(website):
        print(f"ACCESS DENIED: {website} is blocked!")
    else:
        print(f"ACCESS GRANTED: Opening {website}...")

if __name__ == "__main__":
    main()
