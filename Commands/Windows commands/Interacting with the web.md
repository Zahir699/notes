```
Invoke-WebRequest -Uri "https://website-to-visit" -Method GET ---> Utilizes Invoke-WebRequest to browse to a website and issue a GET request.

Invoke-WebRequest -Uri "https://website-to-visit.html" -Method GET <PIPE> fl Images ---> Issues a GET request to the site specified and then pipes the output to format a list of all image files listed in the site.

Invoke-WebRequest -Uri "https://website-to-visit\file.ps1" -OutFile "C:\<filename>" ---> Downloads a file from the website and writes it to disk with -Outfile.

(New-Object Net.WebClient).DownloadFile("https://website-to-visit\tools.zip", "Tools.zip") ---> Uses the .NET string Net.WebClient to download a file from the URL specified.
```