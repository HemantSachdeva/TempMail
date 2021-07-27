<h1 align="center">
  <img src="images/logo.png">
</h1>
<p align="center"> A temporary email right from your terminal written in bash</p><br>

`tempmail` is a command line utility written in `bash` that allows you to create a temporary email address
and receive emails to the temporary email address. It uses 1secmail's [API](https://www.1secmail.com/api/)
to receive emails.

By default `w3m` is used to render the HTML emails on the terminal.
But if you prefer another text based web browser or would rather view the email in a GUI web browser such as Firefox, simply
use the `--browser` or `-b` argument followed by the command needed to launch the web browser of your choice.

<br>
<br>

## Dependencies
- `w3m`
- `curl`
- [`jq`](https://github.com/stedolan/jq)

## Installation

```bash
# Download the tempmail file and make it executable
$ curl -L "https://git.io/tempmail" > tempmail && chmod +x tempmail

# Then move it somewhere in your $PATH. Here is an example:
$ mv tempmail ~/bin/ || sudo mv tempmail /bin/
```

## Usage
```console
$ tempmail --help
tempmail
tempmail -h | -v | -l | -d
tempmail -g [ADDRESS]
tempmail [-t | -b BROWSER] -r | ID

When called with one argument, tempmail
shows the email message with specified ID.

-b, --browser BROWSER
        Specify BROWSER (default: w3m) that is used to render the HTML of
        the email
-l, --list
        List all the received emails
-d, --directory
        Set a custom directory to store everything related to 'tempmail'
-g, --generate [ADDRESS]
        Generate a new email address, either the specified ADDRESS, or
        randomly create one
-h, --help
        Show help
-r, --recent
        View the most recent email message
-t, --text
        View the email as raw text, where all the HTML tags are removed.
        Without this option, HTML is used.
-v, --version
        Show version
```

### Examples
Create random email
```console
$ tempmail --generate
gibrish@1secmail.net
```

Create custom email
```console
$ tempmail --generate mycustomemail@1secmail.com
custom@1secmail.com
```

View the inbox
```console
$ tempmail
[ Inbox for custom@1secmail.com ]

77229944   username@example.com   Test Email
```

View the email
```console
$ tempmail 77229944
```

View the most recent email
```console
$ tempmail -r
```

View emails as pure text
```console
$ tempmail -t 77229944
To: custom@1secmail.com
From: username@example.com
Subject: Greetings from Temp Mail

Hello Temp Mail service user.

[Attachments]
logo.png
```

## Credits
This script is heavily inspired by [Mitch Weaver](https://github.com/mitchweaver)'s `1secmail` script
