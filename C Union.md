Is exactly the same as a [[C Struct]] except the offset of each member is 0 from the beginning of the memory space of the union. This means that every member occupies the same space! A consequence of this is that you can only have one member occupy that space at a time.
Unions may not be compared.
> [!Example]
> ```
> struct athlete {
> 	char name[20];
> 	int jerseynum;
> 	char team[20];
> 	int player_type;
> 	union sportspecific {
> 		struct footballer {...} footballstats;
> 		struct baseballer {...} baseballstats;
> 		struct basketballer {...} basketballstats;
> 	} thesport;
> } theplayer;
> ```
This organization allows for pseudopolymorphic behavior