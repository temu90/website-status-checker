# website-status-checker
# Python tool to check if websites are online
import requests

def check_website(url):
    try:
        headers = {
            "User-Agent": "Mozilla/5.0"
        }
        response = requests.get(url, headers=headers, timeout=5)

        if response.status_code == 200:
            print(f"{url} is UP ✅")
        else:
            print(f"{url} is DOWN ⚠️ (Status: {response.status_code})")

    except requests.exceptions.RequestException as e:
        print(f"{url} is NOT reachable ❌")
        print("Error:", e)

websites = [
    "https://www.your_website_here.com/"
]

for site in websites:
    check_website(site)
