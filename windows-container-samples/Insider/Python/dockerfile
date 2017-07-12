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
