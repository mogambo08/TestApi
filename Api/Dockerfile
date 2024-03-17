#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /src
COPY ["Api.csproj", "."]
RUN dotnet restore "./Api.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "Api.csproj" -c Release -o /app/build


RUN dotnet publish --no-restore -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Api.dll"]