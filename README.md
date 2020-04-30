# twitter-scraper

## dependencies

Before set up, we need to install a few dependencies that this project uses.

**Jupyter Notebook** - `pip install notebook`

**Tweepy** - `pip install tweepy`

After installing dependencies, follow the next steps to properly run the code.

## set up
 
1. Clone the repo and cd into it. `git clone https://github.com/lucasxsong/twitter-scraper.git && cd twitter-scrapper`
2. run `jupyter notebook`. An instance of jupyter notebook should start in your terminal.
3. Navigate to the newly started notebook server on your laptop (eg: localhost:8888/notebooks).
4. Open the `scraper.ipynb` notebook.
5. Run all cells.
6. The stream should take in tweets and write them to the /tweets folder

## configuration

Here are a description of some of the variables that help change the functionality of the streamer. 

**filesize**: determines how big the individual files will be

**numfiles**: determines how many files you will write 

**ofilename**: determines the naming scheme of the files that will be written

**l**: determines the area where the streamlistener will be looking for tweets

## useful links 

- [hiding api keys](https://towardsdatascience.com/how-to-hide-your-api-keys-in-python-fb2e1a61b0a0)
