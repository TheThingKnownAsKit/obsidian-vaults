Init mutex at start of duplicator(), destroy at end
Want to lock after the first thing has been copied, so just put it in the if statement
Unlock at the end of copying if statement

![[Pasted image 20241030130112.png]]
![[Pasted image 20241030130124.png]]
![[Pasted image 20241030130135.png]]

