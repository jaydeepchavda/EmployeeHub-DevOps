#Build stage

#build image
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

COPY RHWalks.API.csproj .

RUN dotnet restore RHWalks.API.csproj

COPY . .

RUN dotnet publish RHWalks.API.csproj -c Release -o /app/publish /p:UseAppHost=false



#Runtime stage

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime


WORKDIR /app

COPY --from=build /app/publish .

EXPOSE 5033

ENTRYPOINT [ "dotnet" , "RHWalks.API.dll" ]