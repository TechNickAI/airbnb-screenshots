# Pull Airbnb Screenshots

A simple tool to grab pages in bulk from Airbnb for auditing purposes, for Airbnb employees only (it won't work unless you have an internal airbnb login).

## Installation
There are a few dependencies to set up. This is a one time setup for each computer.

### Dependencies
1. Brew (to install node.js and other goodies). To install brew, open up Terminal and run: `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`, and follow the instructions
2. Install node with `brew install node`. To confirm it worked, run `node -v`


### Installing airbnb-screenshots
1. Clone this repository by running `git clone https://github.com/gorillamania/airbnb-screenshots.git` If you haven't installed `git` yet, you will be prompted with instructions on how to do so
2. Run `cd airbnb-screenshots; npm install` to install the required packages


#### Chrome Extension for getting Airbnb cookies
 
The tricky part to getting this to work was passing the login cookies to the browser that is doing the screenshots. The solution (if you can call it that) that I used was to use a Chrome extension called [Edit This Cookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=en). It has an export that will give you all the cookies for a given website.

To get your Airbnb cookies:

1. Install the chrome extension
2. Visit airbnb.com. Log in.
3. Click on the Cookie in the toolbar. Click "Export". This will copy the cookies to the clipboard. Save this to a text file (using Textedit). Recommend `cookies.json` as the name of the file.

#### Running
1. Create the CSV file with the reservation ids. 1 column. For a sample format, see [media/sample_reservations.csv](media/sample_reservations.csv)
2. From terminal, cd into the directory where you cloned the repository (if you haven't already) (`cd airbnb-screenshots`) and run `./grab --cookie-jar=$cookieFile $inputfile $outputDir`, where $cookieFile is the file you created from Cookie Jar. $inputFile is the CSV you created, and $outputDir is the directory where you want to have the files saved.

This will open the CSV file and fetch the reservation detail page for each reservation, saving it as $resid.png in the output directory.
