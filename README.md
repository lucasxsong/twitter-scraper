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



## Available APIs For Use

Erik: 

    API key:
    AWNw8Ante1PdYZNW8EpScYoit

    API secret key:
    VX5vZ9GbCNPF677YJL5IhcjjE4ND0NcXmXjpou4mjqfKBUYtKf

    Access token:
    2842012114-JFEgl6EeEELhnPI3fs8XmmVPCw35IKE0u5nFced

    Access token secret:
    bZwLTNDAfvtYYhPhDuJl5prY61sTo6XWGk8ZNT5FLgrvy
    
Kiet: ** Kiet **
    
    API keys = 14t5dj2XpJntlmUJSaSosD1AH
    API secret key = zkWoqA6xp02hg1IeNUwL2AKASYEb6p2gGkGfOPDrPNbJRInP9L
    
    Access Token = 2462026471-CN6KCwnwfWQ08xkhh1he4kdFnXvZeGAagQf3rDJ
    Access Token Secret = TrgSehJEMMCGwp48aIoAkOsQ57h8LLJoqsxlnQG8cRVNM

Nick: 
```
consumer_key = "a4r4DVL2wiu7r5mUE1iFY4mRI"
consumer_secret = "PWscHlly5NMRUlsuPd6bKtzXNipfxAoDQPJDijX2wlNCwgOPGw"
access_token = "958937785791991808-UkIpG4Kqmzag9fRQat2VFOVBIykPbya"
access_token_secret = "hg7VSVaGGtHyhWAUTnY37GyZe5l2g3QPOxjLfDNSSejY8"
```

## Using the Title Scraper

### tl;dr

**Make sure your tweet files end in a complete tweet.** Change into your tweet directory (`os.chdir`). Change output directory (`odir`). 

### Preprocessing

**IMPORTANT** Make sure that all the files that will be scraping from are complete. The last tweet should have have successfully written, closing with something like `"symbols": []}}]}`. If the last tweet in a file is not complete, delete it. Otherwise, we will not be able to read the file in as a json.


    ```
    {"tweet": [{"created_at": "Thu Apr 30 04:30:44 +0000 2020", "text": "@Doiran3 But the unemployment checks are juicy", "user": {"id": 389945480, "id_str": "389945480", "name": "Hawks\u2615\ufe0f\ud83d\udd1bTTV", "screen_name": "TheAdamHawk", "location": "Pitt\u2708\ufe0fLA / Subscribe \u2b07\ufe0f", "url": "https://www.youtube.com/nerdybit?sub_confirmation=1", "description": "I'm an Idea Guy. Internet Personality. Coffee Addict. \ud83d\udc31 Cant Sleep? Get In here http://twitch.tv/theadamhawk \ud83d\udc31 @MLC_Gaming_", "translator_type": "none", "protected": false, "verified
    ```

an example of a non complete tweet, delete.

If this is the first time running the code on the kernel, change the `os.chdir("tweets")` to the directory that you will be converting tweets from. If you are not sure that you are in the right directory, comment out the `for f in files` for loop, and call `print(directory)` to print you roworking directory.

Once you are in the right directory, changing your output directory (`odir`) to the directory that you will be writing to. Take care not to overwrite someone else's converted tweets.

### Processing

When you run the scraper, it will display messages occasionally to show the status of the scraper. An explanation of a few common messages follow:

`Request timed out`: Request to the webserver pointed to by the URL did not succeed in 1.5s. We will just return the title of the page as null ("")

`Exception: ...`: Some other miscellaneous exception happened while pinging for a response. 

`Formatting {file}.txt...`: If you notice that the program is stuck on this line for a while, check your file. If the file has a bunch of errant commas, this is because the formatting tool was repeately called as it could not be read as json. In this case, replace the comma'd file with the original one from Github, and check that the last line of the file is complete.

