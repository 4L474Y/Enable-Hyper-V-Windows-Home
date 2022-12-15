# Enable-Hyper-V-Windows-Home
Script to enable Hyper V on Windows 10 + 11 Home

pushd "%~dp0"



dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt



for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"



del hyper-v.txt



Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL



pause
