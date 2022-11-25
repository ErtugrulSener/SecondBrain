# Types of records

## NS Record

This is where all the DNS records will live. NS records point to your "control center" where all the other DNS records are.

To change them, you have to make changes where your nameserver is hosted.

Examples:

jeff.ns.cloudflare.com

anne.ns.cloudflare.com

There are regulary 2 NS records, some times there are more.

## A Record

A record that points to your website hosting servers, so if someone for example types in "google.com", the A record points to the ip address 172.217.164.142. A records get you directed to the right place, you can view them as an 'alias' instead of needing to type the whole ip adress.

The two fields you will see the Domain and the IP Address.

You can not have duplicated names, so having 2 A records pointing to "google.com" would not be valid.

What's possible is to point any sub domain of the domain via an A record to another ip.

## MX Record (Mail Exchange Record)

An MX record points to an email hosting provider, for example: Office365, Exchange, Zoho or G-Suite.

Mostly this records are preconfigured when you are buying a domain from your provider.

## CNAME Record

Refer to an alias or redirect for a specific site or subdomain. It has two fields:

Name

Destination

It's typical to point the Name "www" to the root domain.

## TXT Record

Used to prove that you own you domain, they associate text with your domain and are informational.