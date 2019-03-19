FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY ["aws-dynamodb-net-core-demo/aws-dynamodb-net-core-demo.csproj", "aws-dynamodb-net-core-demo/"]
RUN dotnet restore "aws-dynamodb-net-core-demo/aws-dynamodb-net-core-demo.csproj"
COPY . .
WORKDIR "/src/aws-dynamodb-net-core-demo"
RUN dotnet build "aws-dynamodb-net-core-demo.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "aws-dynamodb-net-core-demo.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "aws-dynamodb-net-core-demo.dll"]