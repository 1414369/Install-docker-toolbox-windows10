# Install-docker-toolbox-windows10
Bluestack or VirtualBox can not be lauched with Docker which includes Hyper-V on Windows 10. </br >
The solution is to install Docker Toolbox but there is a problem.

## The error
> Docker: error during connect: Post http://%2F%2F.%2Fpipe%2Fdocker_engine/v1.37/containers/create: open //./pipe/docker_engine: The system cannot find the file specified. In the default daemon configuration on Windows, the docker client must be run elevated to connect. This error may also indicate that the docker daemon is not running.
See 'docker run --help'.

## Solution
#### 1) For Windows 7 Command Window(cmd.exe), open cmd.exe with run as administrator and execute following command:
> docker-machine env --shell cmd default

You will receive following output:

> SET DOCKER_TLS_VERIFY=1 </br >
SET DOCKER_HOST=tcp://192.168.99.100:2376</br >
SET DOCKER_CERT_PATH=C:\Users\USER_NAME\.docker\machine\machines\default</br >
SET DOCKER_MACHINE_NAME=default</br >
SET COMPOSE_CONVERT_WINDOWS_PATHS=true</br >
REM Run this command to configure your shell:</br >
REM @FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i</br >

Copy the command below and execute on cmd:
> @FOR /f "tokens=*" %i IN ('docker-machine env --shell cmd default') DO @%i

And then execute following command to control:

> docker version

#### 2) For Windows 7 Powershell, open powershell.exe with run as administrator and execute following command:

> docker-machine env --shell=powershell | Invoke-Expression

And then execute following command to control:

> docker version

## Credit: 
> https://stackoverflow.com/questions/40459280/docker-cannot-start-on-windows
