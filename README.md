# Telegram-Bot
### Author: Julia Volpe

This project uses Python scripts to parse a Telegram chat history backup (`JSON`) into tabular format (`CSV`). The instructions below are how to create your own `.json` and `.csv` files using your own personal Telegram messages. I include my own example in the given files where I created a hypothetical Telegram conversation with words, photos, and files.


## How to use it
Create venv & install requirements in your terminal:
```
python3 -m venv venv

source venv/bin/activate

pip install -r requirements.txt`
```
To be able to see the export chat history option in your Telegram chat settings, you must download and run the correct desktop version of telegram. Here is the link: https://telegram.org/dl/desktop/mac

Once downloaded and running, go to the chat you want to parse, click on the options button (three dots in the upper right corner) and them click on `Export chat history`. In the dialog window, right next to `Format`, chose `JSON`. After the backup is completed, Telegram will generate a `result.json` file. Next you need to copy or move it to script directory.

Use this command if you want to run the original script that converts the entire JSON to CSV:

`python3 telegram_parser.py result.json`

For each chat backup in `result.json`, a `.csv` file will be created in the same directory. The output filename is a stripped down version of the actual chat name (only letters and numbers are kept).

## The output format
Once the script is done parsing, the result `CSV` file will have the format bellow:

- `msg_id`: the unique identifier of the message

- `sender`: the literal name of the sender

- `sender_id`: the unique identifier of the sender

- `reply_to_mesg_id`: if the message is a reply, this column will store the id of that message, or -1 otherwise

- `date`: date time stamp of the message

- `msg_type`: can be one of the following: `text, sticker, file, photo, poll, location or link`

- `msg_content`: the text content the message, already cleaned in terms of newline and spaces; if the message was not a text (sticker, media, etc) this field will store the path pointing to the media

- `has_mention`: it will be `1` if there's a mention in the text, `0` otherwise

- `has_email`: it will be `1` if there's a email in the text, `0` otherwise

- `has_phone`: it will be `1` if there's a phone contact in the message, `0` otherwise

- `has_hashtag`: it will be `1` if there's a hashtag in the text, `0` otherwise

- `is_bot_command`: it will be `1` if the message is a bot command, `0` otherwise

### Contributing
The original script author is Artur Rodrigues Rocha Neto @ https://github.com/keizerzilla 
