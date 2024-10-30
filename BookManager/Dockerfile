# Etapa de build com imagem slim
FROM mcr.microsoft.com/dotnet/sdk:6.0-slim AS build
WORKDIR /source

# Copia e restaura dependências
COPY . .
RUN dotnet restore --no-cache

# Publica a aplicação
RUN dotnet publish -c release -o /app

# Etapa de runtime com imagem slim
FROM mcr.microsoft.com/dotnet/aspnet:6.0-slim
WORKDIR /app
COPY --from=build /app ./

# Expõe a porta 80 para o tráfego HTTP
EXPOSE 80

# Define o entrypoint
ENTRYPOINT ["dotnet", "BookManager.dll"]
