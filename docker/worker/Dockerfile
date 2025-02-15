FROM mcr.microsoft.com/dotnet/sdk:8.0 AS builder
WORKDIR /tmp
COPY . .
RUN dotnet restore
RUN dotnet publish

# app image
FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /tmp
COPY --from=builder /tmp .
ENTRYPOINT ["dotnet", "Worker.dll"]