---
title: "クロス プラットフォーム ツールによる NuGet パッケージの作成"
description: "クロス プラットフォーム ツールによる NuGet パッケージの作成"
keywords: .NET, .NET Core, NuGet
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
translationtype: Human Translation
ms.sourcegitcommit: 300a0304e316cfa265634a3faf74c81c7a8a5e08
ms.openlocfilehash: d863587fbfee2bf713f8566a3e5b294d49ae50e9

---

# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>クロスプラットフォーム ツールを使用して NuGet パッケージを作成する方法

> [!NOTE]
> 以下は、Unix を使用する場合のコマンド ライン サンプルです。  ここに示されている `dotnet pack` コマンドは Windows でも同じように機能します。

.NET Core 1.0 では、ライブラリは NuGet パッケージとして配布する必要があります。  実際に、.NET Standard ライブラリはすべてそのように配布され、使用されています。  `dotnet pack` コマンドを使用して行うのが最も簡単です。

たとえば、NuGet 経由で配布する新しい優れたライブラリを作成したとします。  クロス プラットフォーム ツールを使用して NuGet パッケージを作成すれば、正確に実行できます。  次の例では、`netstandard1.0` をターゲットとする **SuperAwesomeLibrary** というライブラリを想定します。

推移的依存関係がある (つまり、別のプロジェクトに依存するプロジェクトがある) 場合、NuGet パッケージを作成する前に `dotnet restore` コマンドでソリューション全体のパッケージを復元する必要があります。  そうしないと、`dotnet pack` コマンドが正しく機能しません。

パッケージが復元されたことを確認したら、以下のコマンドを実行してライブラリがあるディレクトリに移動できます。

`$ cd src/SuperAwesomeLibrary`

その後、コマンド ラインから以下の 1 つのコマンドのみを実行します。
    
`$ dotnet pack`

これで `/bin/Debug` フォルダーは次のようになります。

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

この場合、デバッグ可能なパッケージが生成されることに注意してください。  リリース バイナリと共に NuGet パッケージをビルドする場合、`-c`/`--configuration` スイッチを追加して、引数として `release` を使用するだけです。

`$ dotnet pack --configuration release`

これで、`/bin` フォルダーに、NuGet パッケージとリリース バイナリを含む `release` フォルダーが生成されます。

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

これで、NuGet パッケージを発行するために必要なファイルが準備できました。

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>`dotnet pack`と `dotnet publish` を混同しないようにしてください

ここで `dotnet publish` コマンドを使用しても意味がありません。  `dotnet publish` コマンドは、同じバンドルにすべての依存関係があるアプリケーションを配置するためのものであり、NuGet 経由で配布して使用する NuGet パッケージを生成するためのものではありません。



<!--HONumber=Nov16_HO3-->


