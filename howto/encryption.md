---
layout: concertina
title: Encryption
description: How to Send/Receive encrypted email
---

# {{ page.title }}

How to Send/Receive encrypted email (OpenPGP, GnuPG, S/MIME)

## Basics

### Cryptology

Cryptology ensures privacy, integrity and authenticity of your data
and communication.

* If you are signing your email the recipient is able to validate
  content and sender. The recipient can be sure, that the received
  message has been send by the person and the content hasn't been
  manipulate. 
* If you encrypt a message, the message can just be read by the
  recipient. You are able to protect your privacy.

## Cryptology via OpenPGP / GnuPG

### Overview

OpenPGP is a Standard defined in RFCs. GnuPG is a software to
implement those standards. 

### Generate a key-pair

Use `gpg --full-gen-key` to generate a key-pair for GnuPG.
After generating the key, you can display the private keys via `gpg
--keyid-format 0xlong -K --fingerprint`.

### Setup Neomutt

	set crypt_use_gpgme=yes
	set postpone_encrypt = yes
	set pgp_self_encrypt = yes
	set crypt_use_pka = no
	set crypt_autosign = no
	set crypt_autoencrypt = no
	set crypt_autopgp = yes 
	set pgp_sign_as=0x12345678

## Good to know

	send2-hook . unset pgp_sign_as
	send2-hook '~f box1@domain.tld' set pgp_sign_as=0x12345678
	send2-hook '~f box2@domain.tld' set pgp_sign_as=0x87654321


