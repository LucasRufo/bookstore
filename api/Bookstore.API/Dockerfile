#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["Bookstore.API/Bookstore.API.csproj", "Bookstore.API/"]
RUN dotnet restore "Bookstore.API/Bookstore.API.csproj"
COPY . .
WORKDIR "/src/Bookstore.API"
RUN dotnet build "Bookstore.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Bookstore.API.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Bookstore.API.dll"]