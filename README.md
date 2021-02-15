# RestApi
Bla! Bla! Bla!

import base64
import requests
from github import Github
from pprint import pprint

username = "Lyminekx"
url = f"https://api.github.com/users/Lyminekx"
g = Github()

user = g.get_user(username)
user_data = requests.get(url).json()


for repo in requests.get(url).json():
    print(user_data)

for repo in user.get_repos():
    print(repo)

def print_repo(repo):
    
    print("Full name:", repo.full_name)
    print("Description:", repo.description)
    print("Date created:", repo.created_at)
    print("Date of last push:", repo.pushed_at)
    print("Home Page:", repo.homepage)
    print("Language:", repo.language)
    print("Number of forks:", repo.forks)
    print("number of stars:", repo.stargazers_count)
    print("Contents:")

    for content in repo.get_contents(""):
        print(content)
    try:
        print("License:", base64.b64decode(repo.get_license().content.encode()).decode())
        except:
            pass
