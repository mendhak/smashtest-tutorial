
## Setup 

For this tutorial, you will need Docker and NodeJS already installed.  

### Create a practice directory

Create a directory for this tutorial and cd into it. 

```
mkdir smashtest-tutorial
cd smashtest-tutorial
```

### Get the Gecko webdriver

Get the latest [Firefox Gecko web driver](https://github.com/mozilla/geckodriver/releases).  

On Ubuntu: 

```
wget -c https://github.com/mozilla/geckodriver/releases/download/v0.29.1/geckodriver-v0.29.1-linux64.tar.gz -O - | tar -xz
```

On Windows (Powershell):

```
wget https://github.com/mozilla/geckodriver/releases/download/v0.29.1/geckodriver-v0.29.1-win64.zip -o geckodriver.zip
Expand-Archive geckodriver.zip -DestinationPath .
rm geckodriver.zip
```


### Install Smashtest 

The Smashtest package is available via npm. 

```
npm install
```


## Write your first test

Create a `main.smash` file.  Add these contents: 

```
Open Firefox

    Navigate to 'https://example.com'

        Click ['More information...']
```

Run the test visually

```
npx smashtest --headless=false
```

The `headless=false` opens up a browser window so you can see what is happening.

Now run the test without a visible browser, but with screenshots instead: 

```
npx smashtest --screenshots=true
```

Preview the `smashtest/report.html` file which shows the output with screenshots.


## Write a test interactively

Replace `main.smash`, and put these lines in:

```
Open Firefox

    ~ Navigate to 'https://www.google.com'

```    

Run `npx smashtest` and the browser window will open. The terminal will go into interactive (REPL) mode, and a browser window opens up, because you used `~` above. 

In the terminal you can now type Smashtest commands and try things out. Press enter to proceed to the Google homepage. 

From the terminal, you can click the 'I agree' button. 

```
Click ['I agree']
```

The dialog disappears. 

You can then perform a search. 

```
Type 'hello world[enter]' into 'input'
```

That takes you to a search results page. 

Use `x` to exit the REPL. 

Put what you've learned so far into the `main.smash`

```
Open Firefox

    Navigate to 'https://www.google.com'

        Click ['I agree']

            Type 'hello world[enter]' into 'input'
```

Rerun the test using `npx smashtest --headless=false` and watch the steps in action. 

