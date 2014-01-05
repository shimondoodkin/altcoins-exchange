altcoins-exchange
=================

**basic architecture**:(based on message queue servers idea like zero mq + nodejs)

**matching engine** (with pair names as categories ) - take 1st select matching, 1st version implemented as select from database and two loops in javascript then can be reimplementd in c++. 

**transaction makers** ( move money from one wallet to other wallet in a transaction ) 
in memory transactional database +  front end : make deal:

**live wallets for each currency** ( addresses names are of user wallet addresses or of usernames ) - coind + its front end (list wallets, list)

**deals archive server** with both parities wallet states as serialize before and after
log last 24 hours only in memory database

text files of last deals per user underscore curency pair downloadable freely or by http used by ajax

**web front end**
login with google.
list of currencies as links
ask bid page(s)
wallet page list of funds in every currency
make deal api

deal execution
```text
0 log deal settings.
- is any wallet locked? if locked wait (skip)
1 lock both wallet
- log wallets states
2 execute: enought confirmed fundes + transaction fees? log1, do move 1, log1, log2, do move 2 log2,.
- check expected wallet states.
- log wallets states
3 unlock
- archive deal price for chart view later
```

server recovery method:
look in locked unfinished deals, ask wallet states, guess deal state by it. complete the deals transactions.

the best would be to write all transaction deatails in the address name
and load the transactions list into memory searchable database and on server load reload it

send money back function. 
on sign up for each currency the user is asked to type a return wallet address with sending address as default.

