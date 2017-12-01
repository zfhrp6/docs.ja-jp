---
title: "CLI ツールで .NET Core アプリを展開する"
description: "コマンド ライン インターフェイス (CLI) ツールを使用して .NET Core アプリを展開する方法を説明します。"
keywords: ".NET, .NET Core, .NET Core 展開"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 82ebe16d-5e1c-46cc-91e8-71974296429c
ms.openlocfilehash: fc7a40667c9b0a623bb0ebdf4ad60783fa58e6c5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>コマンド ライン インターフェイス (CLI) ツールを使用して .NET Core アプリを展開する

.NET Core アプリケーションは、アプリケーション バイナリは含むが対象のシステムに .NET Core バイナリが存在することに依存する*フレームワークに依存する展開*か、アプリケーションと .NET Core のバイナリの両方を含む*自己完結型の配置*のいずれかで展開できます。 概要については、「[.NET Core アプリケーション展開](index.md)」を参照してください。

以降のセクションでは、次のような展開を作成するために [.NET Core コマンド ライン インターフェイス ツール](../tools/index.md)を使用する方法を説明します。

- フレームワークに依存する展開
- サードパーティの依存関係を含む、フレームワークに依存する展開
- 自己完結型の展開
- サードパーティの依存関係を含む、自己完結型の展開

コマンド ラインを使用する場合は、任意のプログラム エディターを使用できます。 プログラム エディターが [Visual Studio Code](https://code.visualstudio.com) の場合、**[表示]** > **[統合ターミナル]** を選択して、Visual Studio Code 環境内にコマンド コンソールを開くことができます。

## <a name="framework-dependent-deployment"></a>フレームワークに依存する展開

サードパーティの依存関係を含まない、フレームワークに依存する展開を展開するプロセスには、アプリのビルド、テスト、および発行が含まれます。 C# で記述された次の単純な例は、このプロセスを示しています。 

1. プロジェクトのディレクトリを作成します。

   プロジェクトのディレクトリを作成し、それを現在のディレクトリにします。

1. プロジェクトを作成します。

   コマンド ラインに [dotnet new console](../tools/dotnet-new.md) と入力して、そのディレクトリに新しい C# コンソール プロジェクトを作成します。

1. アプリケーションのソース コードを追加します。

   エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。 テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。 正規表現 `\w+` を使用して、入力テキストの単語を分離します。

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. プロジェクトの依存関係とツールを更新します。
 
   実行、 [dotnet 復元](../tools/dotnet-restore.md)([注を参照してください](#dotnet-restore-note))、プロジェクトで指定された依存関係を復元するコマンド。

1. アプリのデバッグ ビルドを作成します。

   [dotnet build](../tools/dotnet-build.md) コマンドを使用すると、アプリケーションをビルドでき、[dotnet run](../tools/dotnet-run.md) コマンドを使用すると、それをビルドして実行できます。

1. アプリを展開します。

   プログラムをテストし、デバッグした後は、次のコマンドを使用して、展開を作成します。

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   これにより、リリース (デバッグではなく) バージョンのアプリが作成されます。 作成されたファイルは、プロジェクトの *bin* ディレクトリのサブディレクトリ内にある *publish* という名前のディレクトリに配置されます。

アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。 これは、アプリケーションのファイルと一緒には配布しないよう選択できます。 ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。

アプリケーション ファイルの完全なセットは、任意の方法で展開できます。 たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。 一度インストールすると、ユーザーは `dotnet` コマンドを使用して、`dotnet fdd.dll` などのアプリケーションのファイル名を入力してアプリケーションを実行できます。

また、アプリケーション インストールの一環として、インストーラーはアプリケーション バイナリに加えて、共有フレームワーク インストーラーをバンドルするか、または前提条件として共有フレームワークがあるか確認する必要があります。  共有フレームワークをインストールするには、管理者またはルートの権限が必要です。

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>サードパーティの依存関係を含む、フレームワークに依存する展開

1 つ以上のサードパーティの依存関係を備えたフレームワークに依存する展開を展開するには、それらの依存関係がプロジェクトで使用できる必要があります。 実行するには、次の 2 つの追加手順が必要、 `dotnet restore` ([注を参照してください](#dotnet-restore-note)) コマンド。

1. *csproj* ファイルの `<ItemGroup>` セクションに、必要なサードパーティ ライブラリへの参照を追加します。 次の `<ItemGroup>` セクションには、サードパーティ ライブラリとして [Json.NET](http://www.newtonsoft.com/json) への依存関係があります。

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. サードパーティの依存関係を含む NuGet パッケージをまだダウンロードしていない場合は、ダウンロードします。 パッケージをダウンロードするには、実行、 `dotnet restore` ([注を参照してください](#dotnet-restore-note))、依存関係の追加後にコマンド。 発行時に依存関係はローカルの NuGet キャッシュからが解決されるので、システムで使用可能になる必要があります。

サードパーティの依存関係を含む、フレームワークに依存する展開は、サードパーティの依存関係と同じ移植性を持つことに注意してください。 たとえば、サードパーティ ライブラリが macOS のみをサポートする場合、そのアプリを Windows システムに移植することはできません。 この状況は、サードパーティの依存関係自体がネイティブ コードに依存する場合に生じる可能性があります。 このよい例は、[libuv](https://github.com/libuv/libuv) に対してネイティブの依存関係が必要な [Kestrel サーバー](/aspnet/core/fundamentals/servers/kestrel)です。 このようなサードパーティの依存関係を含むアプリケーションに対して FDD が作成されると、発行された出力には、ネイティブの依存関係がサポートする (そして、その NuGet パッケージ内に存在する) 各[ランタイム識別子 (RID)](../rid-catalog.md) のフォルダーが含まれます。

## <a name="simpleSelf"></a> サードパーティの依存関係を含まない、自己完結型の展開

サードパーティの依存関係を含まない自己完結型の展開を展開するプロセスには、プロジェクトの作成、*csproj* ファイルの変更、アプリのビルド、テスト、および発行が含まれます。 C# で記述された次の単純な例は、このプロセスを示しています。 この例では、コマンド ラインから [dotnet ユーティリティ](../tools/dotnet.md)を使用して、自己完結型の展開を作成する方法を示します。

1. プロジェクトのディレクトリを作成します。

   プロジェクトのディレクトリを作成し、それを現在のディレクトリにします。

1. プロジェクトを作成します。

   コマンド ラインに [dotnet new console](../tools/dotnet-new.md) と入力して、そのディレクトリに新しい C# コンソール プロジェクトを作成します。

1. アプリケーションのソース コードを追加します。

   エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。 テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。 正規表現 `\w+` を使用して、入力テキストの単語を分離します。

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. アプリの対象プラットフォームを定義します。

   *csproj* ファイルで、アプリが対象とするプラットフォームを定義する `<RuntimeIdentifiers>` タグを `<PropertyGroup>` セクションに作成し、対象とする各プラットフォームのランタイム識別子 (RID) を指定します。 なお、RID の分離にはセミコロンを追加する必要があることに注意してください。 ランタイム識別子の一覧については、「[Runtime IDentifier catalog](../rid-catalog.md)」 (ランタイム識別子のカタログ) を参照してください。 

   たとえば、次の `<PropertyGroup>` セクションは、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   `<RuntimeIdentifiers>` 要素は、*csproj* ファイルの任意の `<PropertyGroup>` に含めることができます。 *csproj* ファイルの完全なサンプルは、このセクションの後の部分で示しています。

1. プロジェクトの依存関係とツールを更新します。

   実行、 [dotnet 復元](../tools/dotnet-restore.md)([注を参照してください](#dotnet-restore-note))、プロジェクトで指定された依存関係を復元するコマンド。

1. アプリのデバッグ ビルドを作成します。

   コマンド ラインから、[dotnet build](../tools/dotnet-build.md) コマンドを使用します。

1. プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。

   両方の対象プラットフォームに、次のように `dotnet publish` コマンドを使用します。

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   これにより、各ターゲット プラットフォームに対してアプリのリリース (デバッグではなく) バージョンが作成されます。 作成されたファイルは、プロジェクトの *.\bin\Release\netcoreapp1.1\<runtime_identifier>* サブディレクトリにある *publish* という名前のサブディレクトリに配置されます。 各サブディレクトリには、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。

アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。 これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。 ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。

発行したファイルは、任意の方法で展開できます。 たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。

このプロジェクトの完全な *csproj* ファイルを次に示します。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>サードパーティの依存関係を含む、自己完結型の展開

1 つまたは複数のサードパーティの依存関係を含む自己完結型の展開を展開するプロセスには、依存関係の追加が含まれます。 実行するには、次の 2 つの追加手順が必要、 `dotnet restore` ([注を参照してください](#dotnet-restore-note)) コマンド。

1. 任意のサードパーティ ライブラリへの参照を *csproj* ファイルの `<ItemGroup>` セクションに追加します。 次の `<ItemGroup>` セクションは、サードパーティ ライブラリとして Json.NET を使用します。

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. サードパーティの依存関係を含む NuGet パッケージをシステムにまだダウンロードしていない場合は、ダウンロードします。 で、依存関係をアプリに使用できるようにするには実行、 `dotnet restore` ([注を参照してください](#dotnet-restore-note))、依存関係の追加後にコマンド。 発行時に依存関係はローカルの NuGet キャッシュからが解決されるので、システムで使用可能になる必要があります。

このプロジェクトの完全な *csproj* ファイルを次に示します。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

アプリケーションを展開すると、アプリで使用されるすべてのサードパーティの依存関係も、アプリケーション ファイルに含まれています。 アプリが実行されているシステムには、サードパーティ ライブラリは必要ありません。

サードパーティ ライブラリを含む自己完結型の展開は、そのライブラリでサポートされるプラットフォームにのみ展開できます。 これは、フレームワークに依存する展開にサード パーティの依存関係とネイティブの依存関係があり、ネイティブの依存関係はアプリがインストールされたプラットフォームと対応している必要がある場合と似ています。

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a>関連項目

[.NET Core アプリケーションの展開](index.md)   
[.NET Core のランタイム識別子 (RID) のカタログ](../rid-catalog.md)   

