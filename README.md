# TaskManagerApp
TaskManagerApp by Jorgito and Copilot
# Generacion de Secrets para ocultar passwords en Connection String
1.Inicializa la carpeta del proyecto Net para usar "Secrets"
dotnet user-secrets init
(Esto agrega un UserSecretsId en .csproj)

2.Guardar la cadena de conexión completa como secreto
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=azuresqlserverjv.database.windows.net;Database=TaskManagerDB;User Id=TMUser;Password=CodingWolf2026!!;Encrypt=True;"
(Esto guarda el Connection String en el Store de Secrets)

3.Listar los Secrets del Store
dotnet user-secrets list


De esta forma el AppSettings del proyecto Visual Studio no contiene la password en el connection String

En Azure se debe hacer lo siguiete luego de crear el App Service
Entrás a tu App Service → Configuration.
Agregás una variable de entorno con nombre:

	ConnectionStrings__DefaultConnection

Y ahí sí ponés la cadena completa con la contraseña:
	Server=azuresqlserverjv.database.windows.net;Database=TaskManagerDB;User Id=TMUser;Password=<PASSWORD>;Encrypt=True;

El runtime de .NET detecta automáticamente que debe usar esa variable y reemplaza el valor de appsettings.json

