# Base image for the application runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
USER app
WORKDIR /app
EXPOSE 8080
EXPOSE 8081

# Build stage to compile the project
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src

# Correct the path to the .csproj file
COPY ["./GymManagement_API.csproj", "."]
RUN dotnet restore "./GymManagement_API.csproj"

# Copy the rest of the project files
COPY . .
WORKDIR "/src/GymManagement_API"
RUN dotnet build "./GymManagement_API.csproj" -c $BUILD_CONFIGURATION -o /app/build

# Publish the compiled project
FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "GymManagement_API.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

# Final stage to create the runtime image
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "GymManagement_API.dll"]
