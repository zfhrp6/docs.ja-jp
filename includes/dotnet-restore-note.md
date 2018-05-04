> [!NOTE]
> .NET Core 2.0 以降、[`dotnet restore`](~/docs/core/tools/dotnet-restore.md) を実行する必要がなくなりました。`dotnet new`、`dotnet build`、`dotnet run` のような、復元を必要とするあらゆるコマンドによって暗黙的に実行されるためです。
> [Visual Studio Team Services の継続的インテグレーション ビルド](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core)など、明示的な復元が合理的となる一部のシナリオや、復元の時刻を明示的に制御する必要があるビルド システムでは、引き続き有効なコマンドとなります。