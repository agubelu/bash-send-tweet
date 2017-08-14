# Bash tweet sender
A simple Bash script that can be used to easily send automated tweets, without having to rely on an external programming language and/or library. Only `curl` and `OpenSSL` are required, which are installed by default on most systems.

Please keep in mind that the only intended interaction with the Twitter API to be made by this script is to send plain-text tweets. If you wish to perform more complex actions on Twitter through a Bash script, check out [tweet.sh](https://github.com/piroor/tweet.sh).

## Providing user credentials
You'll need a consumer key, consumer secret, access token and access token secret. In case you don't know how to obtain them, you have to register a new application at [Twitter Application Management](https://apps.twitter.com/).

Once you have the required credentials, you can either store them on the main script or on a separate file stored in the same directory: `.twitterkeys`. If you wish to store them directly in the script, then the latter file is not needed.

## How to use the script
### Interactive execution
`./sendtweet`

Executing the script without any arguments or standard input will result in a prompt in which the user can input the text to be tweeted.
### Through a pipe
`somecommand | ./sendtweet`

The output of the piped command (*stdout*) will be tweeted. Receiving a newline will cause it to tweet the previous content and discard any future output.
### Using arguments
`./sendtweet "tweet content"`

The text provided in the first argument will be tweeted, any other arguments will be ignored. This is the preferred way if your tweet contains newlines (since you can pass `$'a tweet\nwith several lines'`). Arguments have preference over piped input.