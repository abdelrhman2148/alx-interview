# 0x06. Star Wars API Project

## Overview

This project involves interacting with the Star Wars API to fetch and display information about Star Wars characters based on the movie ID provided as an argument. You will use JavaScript and Node.js to fetch data from the Star Wars API and display the character names in the order specified by the `/films/` endpoint.

## Requirements

### General Requirements:
- **Allowed editors**: vi, vim, emacs
- All your files will be interpreted on **Ubuntu 20.04 LTS** using **Node.js (version 10.14.x)**.
- All your files should end with a new line.
- The first line of all your files should be exactly `#!/usr/bin/node`.
- Your code should be **semistandard compliant** (using rules of Standard + semicolons on top) and should follow the **Airbnb style guide**.
- All your files must be executable.
- The length of your files will be tested using `wc`.
- You are not allowed to use `var` in your code.

### Specific Requirements:
- Install **Node 10** on your machine:
    ```bash
    $ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
    $ sudo apt-get install -y nodejs
    ```

- Install **semi-standard**:
    ```bash
    $ sudo npm install semistandard --global
    ```

- Install the **request** module:
    ```bash
    $ sudo npm install request --global
    ```

### Task Description:
Write a script that prints all characters of a Star Wars movie. The first positional argument passed should be the Movie ID (e.g., `3` = “Return of the Jedi”).

- Display one character name per line in the same order as the “characters” list in the `/films/` endpoint.
- Use the **Star Wars API** to fetch movie data.
- Use the **request module** to make the API call.

### Example
```bash
$ ./0-starwars_characters.js 3
Luke Skywalker
C-3PO
R2-D2
Darth Vader
Leia Organa
Obi-Wan Kenobi
Chewbacca
Han Solo
Jabba Desilijic Tiure
Wedge Antilles
Yoda
Palpatine
Boba Fett
Lando Calrissian
Ackbar
Mon Mothma
Arvel Crynyd
Wicket Systri Warrick
Nien Nunb
Bib Fortuna
```

### Repo:
- GitHub Repository: [alx-interview](https://github.com/alx-interview)
- Directory: `0x06-starwars_api`
- File: `0-starwars_characters.js`

## Implementation

```javascript
#!/usr/bin/node
const request = require('request');
const movieId = process.argv[2];

// Check if movieId is provided
if (!movieId) {
  console.error('Please provide a movie ID as an argument.');
  process.exit(1);
}

// Set up the options for the API request
const categories = {
  url: 'https://swapi-api.hbtn.io/api/films/' + movieId,
  method: 'GET'
};

// Make the initial request to get the movie details
request(categories, function (error, response, body) {
  if (error) {
    console.error('Failed to fetch movie details:', error);
    return;
  }

  try {
    const characters = JSON.parse(body).characters;

    // Check if characters array is valid and not empty
    if (!characters || characters.length === 0) {
      console.error('No characters found in the API response.');
      return;
    }

    // Start printing characters
    printCharacters(characters, 0);
  } catch (err) {
    console.error('Failed to parse movie details:', err);
  }
});

// Function to print characters recursively
function printCharacters (characters, index) {
  if (index >= characters.length) return;

  request(characters[index], function (error, response, body) {
    if (error) {
      console.error('Failed to fetch character data:', error);
      return;
    }

    try {
      console.log(JSON.parse(body).name);
      printCharacters(characters, index + 1);
    } catch (err) {
      console.error('Failed to parse character data:', err);
    }
  });
}
```

## How to Run

1. Ensure that **Node.js (version 10.14.x)** and the **request module** are installed.
2. Create a file named `0-starwars_characters.js` and paste the code provided.
3. Run the script using the command:
   ```bash
   ./0-starwars_characters.js <Movie_ID>
   ```

For example:
```bash
./0-starwars_characters.js 1
```

This will display the list of character names for the movie with ID `1`.

## Notes

- The script takes the Movie ID as the first positional argument, which is then used to make a request to the Star Wars API's `/films/` endpoint.
- The script makes subsequent requests to fetch character details from the `characters` array returned by the API and prints their names.

## Additional Resources
- **Mock Technical Interview**
- **Star Wars API Documentation**: [Star Wars API Docs](https://swapi.dev/)
