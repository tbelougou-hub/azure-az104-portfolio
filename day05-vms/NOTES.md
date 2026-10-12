# #	Day	05	–	Compute	I	(Virtual	Machines)

**Exam domain:** Compute
**Date completed:** 10/11/2026

## What I built
Deployed	a	B1s	Ubuntu	VM	(labvm1),	connected	to	it	over	SSH,	and	applied	a	Custom	Script
Extension	that	wrote	a	file	to	the	VM	at	deploy	time.	Resized	the	running	VM	live	from
B1s	to	B1ms,	then	created	and	attached	an	additional	4GiB	data	disk	and	confirmed	it	with
lsblk.

## Key commands / concepts used
ssh	@	cat	/tmp/hello.txt	lsblk
echo	"Hello	from	custom	script"	>	/tmp/hello.txt

## What I learned / what surprised me
VM	resizing	and	disk	attachment	can	both	be	done	without	redeploying	the	VM,	though
resizing	is	limited	to	sizes	available	on	that	VM's	current	hardware	cluster.	Custom
Script	Extensions	are	a	lightweight	way	to	bootstrap	a	VM	at	deploy	time	—	a	simple
alternative	to	a	full	configuration	management	tool	for	small	tasks.

## Screenshots
01-vm-running.png
02-custom-script-output.png	
03-data-disk-attached.png