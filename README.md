
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

Create a `main.smash` file.  Add these contents

```
Open Firefox

    Navigate to 'https://example.com'

        Click ['More information...']
```

Now run the test visually

```
npx smashtest --headless=false
```

A browser window is launched, navigates to example.com and clicks "More Information".  The `headless=false` lets you see what is happening.

You can also run the test headless, but view it as a series of screenshots instead.  

```
npx smashtest --screenshots=true
```

Preview the `smashtest/report.html` file, which shows the output with screenshots.


## Write a test interactively

Replace `main.smash`.  Put these contents in

```
Open Firefox

    ~ Navigate to 'https://www.google.com'

```    

Run `npx smashtest` and the browser window will open, and the terminal goes into interactive mode because you used `~` above. 

In the terminal you can now type Smashtest commands more interactively.  

Press enter in the terminal to proceed to the Google homepage. 

You can click the 'I agree' button:

```
Click ['I agree']
```

The dialog disappears. 

You can perform a search: 

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

Rerun the test using `npx smashtest --headless=false` to see the steps in action. 



## Running tests in branches

Write a test which goes to Google's page, but do two different searches at the same indent level.  

```
Open Firefox

    Navigate to 'https://www.google.com'

        Click ['I agree']

            Type 'hello world[enter]' into 'input'

            Type 'hello universe[enter]' into 'input'
```

Run the test with `npx smashtest --headless=false` and two browser windows open.  

Indented instructions happen one after the other. Instructions at the same level, next to each other, create branches which run separately. The above example results in two branches and therefore two browsers.  