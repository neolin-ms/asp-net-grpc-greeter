FROM mcr.microsoft.com/dotnet/sdk:7.0 as build

WORKDIR /src

COPY /Greeter/*.sln .
COPY ./Greeter/Greeter.csproj ./src/Greeter/

RUN dotnet restore

COPY . .

RUN dotnet publish -c Release -o /published Greeter/Greeter.csproj

FROM mcr.microsoft.com/dotnet/aspnet:7.0 as runtime

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "Greeter.dll" ]
