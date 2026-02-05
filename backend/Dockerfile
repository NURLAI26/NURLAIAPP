# 1️⃣ Build stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY NullAI.sln .
COPY NullAI.Api/NullAI.Api.csproj NullAI.Api/
RUN dotnet restore

COPY . .
WORKDIR /src/NullAI.Api
RUN dotnet publish -c Release -o /app/publish

# 2️⃣ Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/publish .

EXPOSE 8080
ENTRYPOINT ["dotnet", "NullAI.Api.dll"]
