* Returning 0 indicates proper exit, anything else indicates bad behavior
* `echo $?` to see previous return value from main
```
int main(int argc, char *argv[]) { return 0; }
int main(int argc, char **argv) { return 0; }
int main(void) { return 0; }
```