---
layout: concertina
title: getmail, procmail and notmuch 
description: getmail, procmail and notmuch 
---

# {{ page.title }}

getmail, procmail and notmuch 

## Overview

This article may helpful for mail-power-users.

This document describes the use of getmail mail retrieval agent (MRA)
to get your mails, procmail  mail delivery agent (MDA) to filter your
mails and notmuch to index your mails and build virtual mailboxes. 

## Configuration

### procmail

	DATE_YEAR=`date +'%Y'`
	MAILDIR=$HOME/.maildir
	PMDIR=$HOME/.procmail
	LOGFILE=$PMDIR/procmaillog
	LOGABSTRACT=yes
	VERBOSE=on
	DEFAULT=$MAILDIR/Archiv/${DATE_YEAR}/

### getmail

	[retriever]
	type = SimpleIMAPSSLRetriever
	server = imap.domain.tld
	username =  your_imap_user
	password = your_imap_passwd
	mailboxes = ("Inbox", "Archive","Sent Items")
	
 	[destination]
 	type = MDA_external
 	path = /usr/bin/procmail
 	arguments = ("-f", "%(sender)")
	
	[options]
	verbose = 1
	read_all = false
	message_log = ~/.getmail/log
	delete_after = 3

### notmuch

	-inbox +NeoMutt 			-- folder:Mailingliste/NeoMutt-Devel
	-inbox +NeoMutt 			-- folder:Mailingliste/NeoMutt-Users
	-inbox +Debian +Debian-User -- folder:Mailingliste/Debian-User-German
	
	+Familie -- from:mama@domain.de
	+Familie -- from:papa@domain.de
	
	+Firma -- from:@meineFirma.de

### neomutt

	set nm_default_uri = "notmuch:///home/user/.maildir"
	set virtual_spoolfile=yes
	unmailboxes *
	virtual-mailboxes "Eingang" "notmuch://?query=tag:inbox"
	virtual-mailboxes "ToDo" "notmuch://?query=tag:todo"
	virtual-mailboxes "Ungelesene E-Mails" "notmuch://?query=tag:unread"
	virtual-mailboxes "NeoMutt" "notmuch://?query=tag:NeoMutt"
	virtual-mailboxes "Debian-User" "notmuch://?query=tag:Debian-User"
	virtual-mailboxes "Sent Folder" "notmuch://?query=folder:Sent"
	virtual-mailboxes "E-Mails mit PDF" "notmuch://?query=attachment:\.pdf"
	virtual-mailboxes "E-Mails mit JPG" "notmuch://?query=attachment:\.jpg%20or%20attachment:\.png"
	virtual-mailboxes "E-Mails von heute" "notmuch://?query=date:today"
	virtual-mailboxes "E-Mails von gestern" "notmuch://?query=date:yesterday"
	virtual-mailboxes "E-Mails von dieser Woche" "notmuch://?query=date:week.."
	virtual-mailboxes "E-Mails von diesem Monat" "notmuch://?query=date:month.."
	virtual-mailboxes "E-Mails von Familie" "notmuch://?query=tag:Familie"

## Details

## Good to know

### Multi Accounts




