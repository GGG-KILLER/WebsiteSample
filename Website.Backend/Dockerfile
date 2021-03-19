#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["Website.Backend.csproj", "."]
RUN dotnet restore "./Website.Backend.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "Website.Backend.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Website.Backend.csproj" -c Release -o /app/publish

FROM base AS final
USER nobody:nobody
WORKDIR /app

COPY --chown=nobody:nobody --from=publish /app/publish .

# Environment settings
ENV ASPNETCORE_ENVIRONMENT Production
ENV ASPNETCORE_URLS http://+:8080

ENTRYPOINT ["dotnet", "Website.Backend.dll"]
