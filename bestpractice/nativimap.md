---
layout: concertina
title: Native IMAP
description: Neomutt with native IMAP 
---

# {{ page.title }}

Neomutt with native IMAP

## Overview

Do you like to try neomutt or you just would like to access your
E-Mails which are stored on an IMAP Server? In this case the native
IMAP Support of neomutt may the best way to access your mails.

## Configuration

The Neomutt team provides an [example configuration
file](https://github.com/neomutt/samples/blob/master/config/neomuttrc-imap-example)
to setup an IMAP Account. You can take a copy of the configuration
file and set your data.

Setting up your name and your E-Mail-Address:

	set realname = "Firstname Lastname"
	set from     = "mailbox@domain.tld"

Setting up `realname` and `from` will set the `From:`-Header:

	From: Firstname Lastname <mailbox@domain.tld> 

The `spoolfile` must be set to the IMAP Server:

	set spoolfile="imaps://imap.domain.tld/"

You may set that the `spoolfile` as one of your mailboxes:

	 mailboxes $spoolfile

There exits two variables for the IMAP user and password:

	set imap_user = "your_imap_user"
	set imap_pass = "your_imap_passwd"

The `smtp_url` can be used to define the SMTP Server  

	set smtp_url  = "smtp://user:pwd@smtp.domain.tld:587"

You may like to store all information on the IMAP Server:

	set folder     = $spoolfile
	set postponed  = "+Drafts"
	set record     = "+Sent"
	set trash      = "+Trash"

	mailboxes $postponed $record $trash

## Start neomutt

If this configuration is not your default setting of neomutt, you can
store the file somewhere and use the `-F` parameter to define fine the
configuration.

	$ neomutt -F neomuttrc-imap

Neomutt will create a connection to your remote IMAP Server displays
the messages in the [index panel](../panel/index.html).

## Details

### Using the cache

## Good to know



