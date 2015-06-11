## bash directory

If your project contains bash scripts (e.g. to update the pdf that you share via Dropbox with you supervisors, or other), put them here.

An example of bash script for mirroring directories between two machines:

```bash
#!/bin/bash

# Update based on timestamp
if [ "$HOSTNAME" = vanoise ]; then
	rsync -avu dutri001@papaya:/media/DATA3/dutri001/projectName/ /media/dutri001/LP_DUTRIEUX_Data/RS/projectName/
	rsync -avu /media/dutri001/LP_DUTRIEUX_Data/RS/projectName/ dutri001@papaya:/media/DATA3/dutri001/projectName/
elif [ "$HOSTNAME" = papaya ]; then
	rsync -avu /media/DATA3/dutri001/projectName/ dutri001@vanoise:/media/dutri001/LP_DUTRIEUX_Data/RS/projectName/
	rsync -avu dutri001@vanoise:/media/dutri001/LP_DUTRIEUX_Data/RS/projectName/ /media/DATA3/dutri001/projectName/
fi
```