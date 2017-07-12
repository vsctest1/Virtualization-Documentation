# Description:

Creates an image containing Python 3.6.2rc2. 

This dockerfile is for demonstration purposes.

# Environment:

Nano Server Insider Base OS Image

# Usage:

**Docker Build**

```
docker build -t python-insider:latest .
```

**Docker Run** 

This will start a container in which you can use the Python cli or run Python scripts.

```
docker run -it python-insider cmd
```

## Dockerfile Details:
```
# escape=`

# Installer image
FROM microsoft/nanoserver-insider-powershell AS installer-env

SHELL ["powershell", "-Command", "$ErrorActionPreference = 'SilentlyContinue';"]

RUN Invoke-WebRequest -Uri https://www.python.org/ftp/python/3.6.2/python-3.6.2rc2-embed-amd64.zip -Outfile python.zip;`
    Expand-Archive python.zip -DestionationPath python; `
    Remove-Item -Force python.zip

#Runtime image 
FROM microsoft/nanoserver-insider

COPY --from=installer-env ["python", "C:\\Program Files\\Python"]

RUN setx PATH "%PATH%;C:\Program Files\Python"
		
```

