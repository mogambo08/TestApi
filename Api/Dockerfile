#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

#FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
#WORKDIR /app
#COPY /bin/release/net8.0/publish .
#ENTRYPOINT ["dotnet", "Api.dll"]
#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.
FROM mcr.microsoft.com/dotnet/core/sdk:8.0 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj .
RUN dotnet restore

# copy everything else and build app
COPY . ./
#WORKDIR /source/aspnetapp
RUN dotnet publish --no-restore -c Release -o /app/publish

# final stage/image
FROM mcr.microsoft.com/dotnet/core/aspnet:8.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Api.dll"]