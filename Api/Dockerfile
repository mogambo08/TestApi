
#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /app
COPY ["TestApi/Api.csproj","Api/"]
COPY ["TestApi/Dto.csproj","Dto/"]
# copy everything else and build app
COPY . .
#WORKDIR /source/aspnetapp
RUN dotnet publish -c Release --property:PublishDir=/out

# final stage/image
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build-env /out .
ENTRYPOINT dotnet Api.dll