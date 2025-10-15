---
aliases:
  - PCB
---
Needed by the [[Operating System|OS]] for each [[Process]], so that if a process is suspended by the [[Scheduler]], it can be restored at a later time
```
enum state_type {new, read, running, waiting, halted}

typedef struct control_block_type {
	enum state_type state;
	address PC;
	int reg_file[NUMREGS];
	struct control_block * next_pcb;
	int priority;
	address memory_footprint;
} control_block;
```

