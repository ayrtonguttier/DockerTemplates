FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
RUN git clone https://github.com/ayrtonguttier/DotNetCacheExample.git
# Caminho deve ser {gitrepo}/{solution}/{project}/{project}.csproj
RUN dotnet restore "./DotNetCacheExample/CacheExample/CacheExample/CacheExample.csproj"
COPY . .
WORKDIR "/src/DotNetCacheExample/CacheExample/CacheExample"
RUN dotnet build "CacheExample.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "CacheExample.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "CacheExample.dll"]
