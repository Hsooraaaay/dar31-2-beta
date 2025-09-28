# dar31-2-beta
Solve updating problem
import requests

topics = ["defi", "layer2", "blockchain"]
headers = {"Accept": "application/vnd.github.v3+json"}

for topic in topics:
    response = requests.get(f"https://api.github.com/search/repositories?q=topic:{topic}&sort=stars&order=desc", headers=headers)
    data = response.json()
    for repo in data["items"][:5]:  # Star top 5 repos per topic
        requests.put(f"https://api.github.com/user/starred/{repo['full_name']}", headers={
            "Authorization": "token YOUR_GITHUB_TOKEN",
            "Accept": "application/vnd.github.v3+json"
        })
        print(f"Starred {repo['full_name']}")
