FROM microsoft/aspnetcore:2.0-jessie AS base
WORKDIR /app
EXPOSE 80
#
#
FROM microsoft/aspnetcore-build:2.0-jessie AS builder
WORKDIR /src
COPY . .
WORKDIR /src/Acerola.UI
RUN dotnet build -c Release -o /app
#
#
FROM builder AS publish
RUN dotnet publish -c Release -o /app
#
#
FROM base AS production
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Acerola.UI.dll"]