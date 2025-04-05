  ## Logan Seeley
![](https://img.shields.io/github/followers/seeleylogan?style=flat&color=rgb(150%2C255%2C150))
![](https://img.shields.io/github/stars/seeleylogan?style=flat&color=rgb(255%2C255%2C50))

```c
person_t user =
{
    .name   = "Logan Seeley",
    .skills = C | OPENGL | PYTHON
};
```
<div class="container">
    <h1>GitHub Follower Count</h1>
    <input type="text" id="username" placeholder="Enter GitHub username" />
    <button onclick="fetchFollowerCount()">Get Follower Count</button>
    <div id="result"></div>
</div>

<script>
    function fetchFollowerCount() {
        const username = document.getElementById("username").value;
        const resultDiv = document.getElementById("result");

        if (username.trim() === "") {
            resultDiv.innerHTML = "<p class='error'>Please enter a username.</p>";
            return;
        }

        const url = `https://api.github.com/users/${username}`;

        fetch(url)
            .then(response => {
                if (!response.ok) {
                    throw new Error("User not found or API error");
                }
                return response.json();
            })
            .then(data => {
                const followerCount = data.followers;
                resultDiv.innerHTML = `<p>User <strong>${username}</strong> has <span class="follower-count">${followerCount}</span> followers.</p>`;
            })
            .catch(error => {
                resultDiv.innerHTML = `<p class='error'>Error: ${error.message}</p>`;
            });
    }
</script>
