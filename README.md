
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

On Windows:

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
