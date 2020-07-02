---
layout: concertina
title: Multi Profile 
description: Use Profiles 
---

# {{ page.title }}

Multi Profiles to setup more than one account

## Overview

You may have more than one account and you like to setup neomutt to
use your accounts. 

Lets assume you have two accounts, your private account and one
business account.

We will create one configuration file for each profile and setup some
hooks to switch the profiles.

Keep in mind, this is just an example. It depends on your context how
many parts you can use.

## Configuration

For each account you can create a profile-configuration e.g.
`~/.neomutt/profile.private` and `~/.neomutt/profile.business`.

You can setup each profile like the example below:

### Profile setup

	set hostname  = "domain.tld"
	set realname  = "Firstname Lastname"
	set from      = "mailbox@domain.tld"
	set signature = "~/.neomutt/signatur.profilename"	
	set smtp_url  ="smtp://user:pwd@smtp.domain.tld"

	color status     brightgreen    blue
	echo "Sending mail as mailbox@domain.tld"

### Hooks

You may create `neomuttrc-hooks` to setup some hooks.

Lets assume your mails are filtered (e.g. procmail) already. You may
have one incoming mailbox for each account. You are able to use
folder-hooks to switch the profile, if you change the mailbox.

	folder-hook "Inbox-Private"  'source ~/.neomutt/profile.private'
	folder-hook "Inbox-Business" 'source ~/.neomutt/profile.business'

You may have some contacts in your alias file:

	alias Lastname.Firstname Firstname Lastname <mailbox@domain.tld>
You can add groups on the accounts.
	
	alias -group AccountPrivate Lastname1.Firstname1 Firstname1 Lastname1 <mailbox1@domain.tld>
	alias -group AccountBusiness Lastname2.Firstname2 Firstname2 Lastname2 <mailbox2@domain.tld>

Now, you can add a send-hook to the groups like:

	send-hook "%C AccountPrivate" 'source ~/.neomutt/profile.private'
	send-hook "%C AccountBusiness" 'source ~/.neomutt/profile.business'

You are able to switch the account, when you replay on a mail.

	reply-hook "~t private@domain.tld" 'source ~/.neomutt/profile.private'

Setting the PGP key via send2-hook.

	send2-hook '~f private@domain.tld'  set pgp_sign_as=0x87654321
	send2-hook '~f business@domain.tld' set pgp_sign_as=0x12345678


## Details

### Using the cache

## Good to know

### Profile status color 

Change the color of status for each account. You can see the switch
between the accounts on neomutt's status color

	color status     brightgreen    red 	# business
	color status     brightgreen    blue	# private

### Echoing

`echo` lets you print messages to the message window. You can use to print the mail address you switched your configuration to.
