# ===========================
# Stage 1: Build the app
# ===========================
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copy everything and restore dependencies
COPY . .
RUN dotnet restore

# Build and publish the application to the /app folder
RUN dotnet publish -c Release -o /app

# ===========================
# Stage 2: Run the app
# ===========================
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

# Copy published files from the build stage
COPY --from=build /app .

# Expose the port the app will run on
EXPOSE 8080

# Set the entry point to run the application
ENTRYPOINT ["dotnet", "Backend.dll"]
