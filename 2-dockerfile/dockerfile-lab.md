# 2. Dockerfile lab

You're working for Cyberdyne Systems, and they have decided to containerize their new application, the firmware for 
the new robot model T-800. There is a Dockerfile to build the application, but it does not run the application. 

For the purposes of the container, Cyberdyne would like the application to built and run in a single container. This means 
that the Dockerfile will need to be a multi-stage build, with multiple FROM statements. The current Dockerfile looks like this:

`FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["UnitHost/UnitHost/UnitHost.csproj", "UnitHost/UnitHost/"]
COPY ["t800/t800.csproj", "t800/"]
RUN dotnet restore "UnitHost/UnitHost/UnitHost.csproj"
COPY . .
WORKDIR "/src/UnitHost/UnitHost"
RUN dotnet build "UnitHost.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "UnitHost.csproj" -c Release -o /app/publish /p:UseAppHost=false
`

This builds the file in a build stage named *build*, and then publishes the results of UnitHost.csproj in Release mode - if we were to use this in a real build, 
we would have a volume mapped for /app so that we could capture the results as an artifact, but that is not what we're concerned with right now.

Your task is to modify the Dockerfile to add an additional stage, *final*, that will actually execute the application inside the container. Once complete, you should see output like this:

*Capturing image...
Deciding...
Capturing image...
Deciding...
Capturing image...
Deciding...
Capturing image...
Deciding...
Capturing image...
Deciding...
Battery depleted. Replace with compatible RTG*

That is the robot running through its decision loop. Modify your Dockerfile, add the *final* stage, then build it using this command:

`docker build -t cyberdyne/t800 -f t800.Dockerfile .`

Making sure that you execute in the same directory as the Dockerfile. This Dockerfile will be the asset to be evaluated for the lab.

## Hint

Visual Studio, a common tool for working with this project's tech stack, generates the Dockerfile to run the application. It might be useful to search for documentation of how it does this.

