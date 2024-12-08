from github import Github
import matplotlib.pyplot as plt
from datetime import datetime

# Replace 'your_github_token' with your GitHub token
GITHUB_TOKEN = 'your_github_token'
g = Github(GITHUB_TOKEN)

# Replace 'your_github_username' with your GitHub username
GITHUB_USERNAME = 'your_github_username'

# Fetch user data
user = g.get_user(GITHUB_USERNAME)

# Fetch repositories
repos = user.get_repos()

# Data for visualization
repo_names = []
stars = []
contributions = []

for repo in repos:
    repo_names.append(repo.name)
    stars.append(repo.stargazers_count)
    contributions.append(repo.get_commits().totalCount)

# Sort data by stars
sorted_data = sorted(zip(repo_names, stars, contributions), key=lambda x: x[1], reverse=True)
repo_names, stars, contributions = zip(*sorted_data)

# Visualization: Bar Chart for Repositories and Stars
plt.figure(figsize=(10, 6))
plt.barh(repo_names, stars, color='skyblue')
plt.xlabel('Stars')
plt.ylabel('Repositories')
plt.title('GitHub Repositories by Stars')
plt.gca().invert_yaxis()
plt.show()

# Visualization: Contributions Pie Chart
plt.figure(figsize=(8, 8))
plt.pie(contributions, labels=repo_names, autopct='%1.1f%%', startangle=140, colors=plt.cm.Paired.colors)
plt.title('Contributions by Repository')
plt.show()

# Display basic profile information
print("GitHub Profile Visualization")
print(f"Username: {user.login}")
print(f"Public Repos: {user.public_repos}")
print(f"Followers: {user.followers}")
print(f"Following: {user.following}")









RedBull Basement 2024 Japan TopFinalist  
　
<!---
hatimaruuuu/hatimaruuuu is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
)
