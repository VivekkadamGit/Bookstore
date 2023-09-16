# Acme BookStore

Acme BookStore is a boilerplate application generated using the ABP.IO platform. It is a bookstore management system built with .NET 7 and PostgreSQL. The repository contains the following main projects:

- **Acme.BookStore.Web**: This is the main front-end application.
- **Acme.BookStore.DbMigrator**: This is a DB migrator used to apply migrations. It should be run once before running the actual application.
- **Acme.BookStore.HttpApi.Host**: This is the API host.

## Prerequisites

- .NET 7.0 SDK
- PostgreSQL
- Node.js and Yarn package manager

## Getting Started

Follow these steps to get the application up and running:

1. **Clone the repository**

   Use the following command to clone the repository:

   ```bash
   git clone https://github.com/Promact/Bookstore.git
   ```

2. **Navigate to the Web project directory**

   ```bash
   cd Bookstore/src/Acme.BookStore.Web
   ```

3. **Restore client-side packages**

   Run the following command to restore the client-side packages:

   ```bash
   yarn
   ```

4. **Update the database connection string**

   Update the connection string in the `appsettings.json` file in the `Acme.BookStore.Web` project to match your PostgreSQL database.

5. **Run the DB Migrator**

   Navigate to the `Acme.BookStore.DbMigrator` directory and run the following command:

   ```bash
   dotnet run
   ```

6. **Run the API host**

   Navigate to the `Acme.BookStore.HttpApi.Host` directory and run the following command:

   ```bash
   dotnet run
   ```

7. **Run the Web project**

   Navigate back to the `Acme.BookStore.Web` directory and run the following command:

   ```bash
   dotnet run
   ```

After following these steps, navigate to `https://localhost:5001` in your web browser to view the application.

## Github Actions

Github actions have "Onpush" running method. whenever new code get push on main branch, it will trigger the github actions.

Github action contains 2 Jobs:
1. Build
2. Deploy

Image fo Github Runner will be "ubuntu-latest"

Build part will download the dependencies via ```dotnet restore``` and build the application via build command ```dotnet build --configuration Release --no-restore ``` and Test the applciation via ```dotnet test --no-restore --verbosity normal```

(Took referance via documentation of Github actions .Net example)

Inside Deploy part.

It will download the dependencies like docker and aws cli.

I have passed allthe sensite data into the secrets of repository inside github actions.

It will build the docker images and then it will get tag to repo and push to it.

## Contributing

We welcome any contributions to the Acme BookStore. Please read our [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
