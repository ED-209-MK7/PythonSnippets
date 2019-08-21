# Snippets of Code

## Python3

### Start a log and write it to functions:

```python
from datetime import datetime,date

LOG = /path/to/something.log

# Start the log file
def startLogFile():
    try:
        now = datetime.utcnow().strftime("%Y-%m-%dT%H:%M:%SZ")
        if not path.isfile(LOG):
            with open(LOG, 'a') as log:
                log.write(now + " - Log Started.\n")
            return('Succeeded')
        else:
            with open(LOG, 'a') as log:
                log.write(now + " - Log Started. Strange, the log file appears to exist already?  Continuing anyways.\n")
            return('Succeeded')
    except:
        return('Failed')
        # For now just simply exit here
        exit(1)

def writeToLog(stringToLog):
    now = datetime.utcnow().strftime("%Y-%m-%dT%H:%M:%SZ")
    with open(LOG, 'a') as log:
        log.write(now + " - " + stringToLog + '\n')
```

### Security Checks on User Input:

```python
from sys import exit, argv

def checkArgs():
    filteredCharacters = [';','&','(',')','>','<']
    listOfNewDevices = getListOfUnaccptedKeys()
    if len(argv) != 2:
        print('Usage: ' + argv[0] + ' [all | altor-name]\n' + '\nDevices to pick from (if only a single one is desired):')
        for device in listOfNewDevices:
            print(device)
        exit(0)
    elif any(character in argv[1] for character in filteredCharacters):
        print('Security Violation. Exiting...')
        exit(0)
    else:
        # Any other args functions from here on....
```

### Check if root:

```python
if geteuid() != 0:
        print(RED + 'You need sudo/root permissions to run this... exiting.' + NOCOLOR)
        exit(0)
```

### Color Printing to the terminal:

```python
# Colors
GREEN = '\033[32m'
RED = '\033[31m'
YELLOW = '\033[33m'
NOCOLOR = '\033[m'

print(GREEN + '[+]' + NOCOLOR + ' The Device is: ' + deviceStatus + '.')
```

### Python Main Function Call and Module Tie in:

```python
main()
if __name__== "__main__":
    main()
```