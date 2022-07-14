# Script for working with service [Evernote](https://evernote.com/intl/ru)

## About
With this script you can interact with [Evernote](https://evernote.com/intl/ru) using API.
You can view your notebooks, notes of a specific notebook and also create a note using a template.


## API

First you need to get an Evernote API Key. 

You can take it [here](https://dev.evernote.com/doc/). 
You need to click on the button `GET AN API KEY`. 
After filling in the information, you will receive `Consumer Key` and `Consumer Secret`.
Also you need to create an account on Evernote development server.

After this you can get Evernote API Token [here](https://dev.evernote.com/get-token/).

Eventually, you should have `Consumer Key`, `Consumer Secret` and `API Token`.

## Configuration

- Python version: 3.10
- Libraries: requirements.txt

## Launch

- Download code
- Through the console in the directory with the code, install the virtual environment with the command:
```bash
python3 -m venv env
```

- Activate the virtual environment with the command:
```bash
source env/bin/activate
```

- Install the libraries with the command:
```bash
pip install -r requirements.txt
```

- Write the environment variables in the `.env` file in the format KEY=VALUE


`EVERNOTE_CONSUMER_KEY` Consumer Key from Evernote API Key

`EVERNOTE_CONSUMER_SECRET` Consumer Secret from Evernote API Key

`EVERNOTE_PERSONAL_TOKEN` API Token from Evernote API Key

`JOURNAL_TEMPLATE_NOTE_GUID` Note ID with template

`JOURNAL_NOTEBOOK_GUID` ID of notebook where you will create notes

`INBOX_NOTEBOOK_GUID` ID of notebook where you will get list of notes

### list_notebooks.py

- To get a list of notebooks in your account, run the script with the command:
```bash
python3 list_notebooks.py
```

You will get list of notebooks:
(Format: notebook_id - notebook_title)
```
9b005151-afff-4d03-a2b6-c0de8e24048b - Первый блокнот
5e78cd70-3953-4f25-8751-82f4b085d06f - Дневник
```
You can take notebook ID to `INBOX_NOTEBOOK_GUID` and `JOURNAL_NOTEBOOK_GUID`.

### dump_inbox.py

- To get a list of notes in your notebook, run the script with the command:
```bash
python3 dump_inbox.py
```

You will get list of notes:
```
--------- 1 ---------
Note ID: 142fc7b8-2a24-48c0-a81d-2152906f2530
Note title: Заметка {date} {dow} # шаблон
Text: 

Какой-то текст2

--------- 2 ---------
Note ID: 50fca824-6c40-4f89-9d3c-3d399d6a7c6c
Note title: Заметка 2022-07-14 четверг
Text: 

Какой-то текст1

Process finished with exit code 0

```
You can take note ID to `JOURNAL_TEMPLATE_NOTE_GUID`.


### add_note2journal.py

First you need add note with template in title: `Заметка {date} {dow} # шаблон`. 
And add ID of this note to `JOURNAL_TEMPLATE_NOTE_GUID`.
- To create note in your notebook, run the script with the command:
```bash
python3 add_note2journal.py
```

- Optional Arguments:
```
date - You can add date to you note. Use format "YYYY-MM-DD" (Default: current day)
```