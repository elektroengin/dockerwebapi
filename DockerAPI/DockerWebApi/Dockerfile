FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

COPY . .

RUN dotnet restore "./DockerWebApi.csproj" --disable-parallel
RUN dotnet publish "./DockerWebApi.csproj" -c relase -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app

COPY --from=build /app ./
EXPOSE 5000

ENTRYPOINT ["dotnet","DockerWebApi.dll"]
