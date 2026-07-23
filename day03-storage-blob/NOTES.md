# Day 03 – 	Storage	I	(Accounts	&	Blob)

**Exam domain:** Storage
**07/22/2026:**

## What I built
Created	a	storage	account	with LRS redundancy	and	a private	blob	
container,	uploaded	a
test	file,	and	moved	it	to	the	Cool	access	tier.	Generated	a	SAS	
token	to	test	scoped,
time-limited	access	to	the	file,	then	regenerated	the	token	without	
Read	permission	and
confirmed	the	URL	was	denied.	Set	up	a	lifecycle	management	rule	to	
automatically	move
blobs	to	the	Cool	tier	after	30	days.

## Key commands / concepts used
Portal	paths	used:	Storage	account	>	Containers	>	+	Container	(Private
access	level)	Container	>	Upload	Blob	>	Change	tier	>	Cool	Blob	>	…
menu	>	Generate	SAS	>	Generate	SAS	token	and	URL	Storage	account >	Lifecycle	management	>	+	Add	a	rule

## What I learned / what surprised me
SAS	tokens	are	permission-scoped	at	generation	time	—	removing	the	
Read	permission	and
regenerating	the	token	immediately	revoked	that	access,	which	is	a	
much	finer-grained
control	than	just	making	the	whole	container	public	or	private.

## Screenshots
![storage/container/blob](01-blob-uploaded.png)
![Generate and test	a SAS token](02-sas-token-config.png)
![Setup	a lifecycle	management rule](03-lifecycle-rule.png)