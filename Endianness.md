Refers to the order in which bytes are stored in memory.
It does not affect the order in which bits or array elements are stored.
![[Pasted image 20250821192508.png]]
> [!hint]-  Lore
The adjective endian has its origin in the writings of 18th century Anglo-Irish writer Jonathan Swift. In the 1726 novel Gulliver's Travels, he portrays the conflict between sects of Lilliputians divided into those breaking the shell of a boiled egg from the big end or from the little end. By analogy, a CPU may read a digital word's big or little end first. 

# Little Endian
Address starts with least significant byte of the word (the normal one 🙂)
"Normal" because it is dominant today. You really only get [[#Big Endian]] for super old [[Instruction Set Architecture]]s... and the [[IP Protocol|Internet]] 😳
# Big Endian
Address starts most significant byte of the word
