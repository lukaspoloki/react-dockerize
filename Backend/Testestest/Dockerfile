FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 5000

ENV ASPNETCORE_URLS=http://+:5000

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["Backend/Testestest/Testestest.csproj", "Backend/Testestest/"]
RUN dotnet restore "Backend\Testestest\Testestest.csproj"
COPY . .
WORKDIR "/src/Backend/Testestest"
RUN dotnet build "Testestest.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Testestest.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Testestest.dll"]
