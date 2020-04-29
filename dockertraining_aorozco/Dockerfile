#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["dockertraining_aorozco/dockertraining_aorozco.csproj", "dockertraining_aorozco/"]
RUN dotnet restore "dockertraining_aorozco/dockertraining_aorozco.csproj"
COPY . .
WORKDIR "/src/dockertraining_aorozco"
RUN dotnet build "dockertraining_aorozco.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "dockertraining_aorozco.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "dockertraining_aorozco.dll"]