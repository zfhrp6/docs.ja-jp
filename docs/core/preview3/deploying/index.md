---
title: ".NET Core アプリケーション展開"
description: ".NET Core アプリケーション展開"
keywords: ".NET, .NET Core, .NET Core 展開"
author: rpetrusha
manager: wpickett
ms.date: 11/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: d99d1a68fd6d1daf68670d6d73c07fe1009d92d9

---

# <a name="net-core-application-deployment"></a>.NET Core アプリケーション展開 #

.NET Core アプリケーションに対して、次の 2 種類の展開を作成できます。 

- フレームワークに依存する展開。 名前が示すように、フレームワークに依存する展開 (FDD) は、ターゲット システムに存在する .NET Core のシステム全体の共有バージョンに依存します。 .NET Core は既に存在するので、アプリは .NET Core のインストール間で移植することもできます。 アプリには、それ自体のコード、および .NET Core ライブラリの外部にあるサードパーティの依存関係のみが含まれています。 FDD には、コマンドラインから [dotnet ユーティリティ](../tools/dotnet.md)を使用して起動できる .dll ファイルが含まれています。 たとえば、`dotnet app.dll` は `app` という名前のアプリケーションを実行します。

- 自己完結型の展開。 FDD とは異なり、自己完結型の展開 (SCD) は、ターゲット システムに存在するいずれの共有コンポーネントにも依存しません。 .NET Core ライブラリと .NET Core ランタイムの両方を含むすべてのコンポーネントがアプリケーションに含まれており、他の .NET Core アプリケーションから分離されています。 SCD には、プラットフォーム固有の .NET Core ホストの名前変更後のバージョンである実行可能ファイル (`app` という名前のアプリケーション用の Windows プラットフォーム上の `app.exe` など)、および実際のアプリケーションである .dll ファイル (`app.dll` など) が含まれています。

## <a name="framework-dependent-deployments-fdd"></a>フレームワークに依存する展開 (FDD) ##

FDD では、アプリ、およびサードパーティの依存関係のみを展開します。 アプリは、ターゲット システムに存在する .NET Core のバージョンを使用するので、.NET Core を展開する必要はありません。 これは、.NET Core アプリの既定の展開モデルです。

### <a name="why-create-a-framework-dependent-deployment"></a>フレームワークに依存する展開を作成する理由 ###

FDD の展開には、次のいくつかの利点があります。

- .NET Core アプリが実行されるターゲットのオペレーティング システムを事前に定義する必要はありません。 .NET Core は、オペレーティング システムに関係なく実行可能ファイルとライブラリに共通の PE ファイル形式を使用するので、.NET Core は、基になるオペレーティング システムに関係なくアプリを実行できます。 PE ファイル形式の詳細については、「[.NET Assembly File Format](../../../standard/assembly-format.md)」 (.NET アセンブリのファイル形式) を参照してください。

- 展開パッケージは小サイズです。 .NET Core 自体ではなく、アプリとその依存関係のみを展開する必要があります。

- 複数のアプリが、同じ .NET Core インストールを使用します。これにより、ホスト システム上のディスク領域とメモリ使用量の両方が削減されます。

次のいくつかの短所もあります。

- ターゲットとする .NET Core のバージョンまたはそれ以降のバージョンがホスト システムに既にインストールされている場合にのみ、アプリを実行できます。

- 将来のリリースでは、ユーザーの認識なしに .NET Core ランタイムおよびライブラリが変更される場合があります。 まれなケースでは、アプリのビヘイビアーが変更される可能性があります。

### <a name="deploying-a-framework-dependent-deployment"></a>フレームワークに依存する展開を展開する ###

サードパーティの依存関係を含まない、フレームワークに依存する展開を展開するプロセスには、アプリのビルド、テスト、および発行が含まれます。 C# で記述された次の単純な例は、このプロセスを示しています。 この例では、コマンドラインの [dotnet ユーティリティ](../tools/dotnet.md)を使用しますが、Visual Studio や Visual Studio Code などの開発環境を使用して、この例をコンパイル、テスト、および発行することもできます。

1. プロジェクトのディレクトリを作成し、コマンドラインから [dotnet new](../tools/dotnet-new.md) と入力して、新しい C# コンソール プロジェクトを作成します。

2. エディターで `Program.cs` ファイルを開き、自動生成されたコードを次のコードに置き換えます。 テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。 正規表現 `\w+` を使用して、入力テキストの単語を分離します。

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else
              {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. [dotnet restore](../tools/dotnet-restore.md) コマンドを実行して、プロジェクトで指定された依存関係を復元します。

4. [dotnet build](../tools/dotnet-build.md) コマンドを使用して、アプリのデバッグ ビルドを作成します。

5. プログラムをデバッグしてテストしたら、`dotnet publish -f netcoreapp1.0 -c release` コマンドを使用して、アプリで展開するファイルを作成できます。 これにより、リリース (デバッグではなく) バージョンのアプリが作成されます。

   作成されたファイルは、プロジェクトの `.\bin\release\netcoreapp1.0` サブディレクトリのサブディレクトリ内にある、`publish` という名前のディレクトリに配置されます。

6. アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。アプリケーションのファイルと共にパッケージ化しないように選択することもできます。

アプリケーション ファイルの完全なセットを任意の方法で展開できます。 たとえば、zip ファイル内にパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。

また、アプリケーション インストールの一環として、インストーラーはアプリケーション バイナリに加えて、共有フレームワーク インストーラーをバンドルするか、または前提条件として共有フレームワークがあるか確認する必要があります。  共有フレームワークのインストールは、コンピューター全体が対象なので、管理者/ルート アクセスを必要とします。

### <a name="deploying-a-framework-dependent-deployment-with-third-party-dependencies"></a>サードパーティの依存関係を含む、フレームワークに依存する展開を展開する ###

1 つまたは複数のサードパーティの依存関係を含む、フレームワークに依存する展開を展開するプロセスでは、`dotnet restore` コマンドを実行できるようにするために、次の 3 つの追加手順を実行します。

1. 任意のサードパーティ ライブラリへの参照を `csproj` ファイルの `<ItemGroup>` セクションに追加します。 次の `<ItemGroup>` のセクションでは、既定のプロジェクトに依存関係を含む、Json.NET をサード パーティ製のライブラリとする、`<ItemGroup>` を示します。

    ```xml
      <ItemGroup>
        <PackageReference Include="Microsoft.NETCore.App">
          <Version>1.0.1</Version>
        </PackageReference>
        <PackageReference Include="Newtonsoft.Json">
          <Version>9.0.1</Version>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Sdk">
          <Version>1.0.0-alpha-20161102-2</Version>
          <PrivateAssets>All</PrivateAssets>
        </PackageReference>
      </ItemGroup>
    ```

上の例では、SDK の依存関係は残っています。 コマンド ライン ツールが機能するには、必要なすべてのターゲットを復元する必要があるため、この依存関係は仕様で必要です。  

2. サードパーティの依存関係を含む NuGet パッケージをまだダウンロードしていない場合は、ダウンロードします。 パッケージをダウンロードするには、依存関係を追加した後で `dotnet restore` コマンドを実行します。 発行時に依存関係はローカルの NuGet キャッシュからが解決されるので、システムで使用可能になる必要があります。

サードパーティの依存関係を含む、フレームワークに依存する展開は、サードパーティの依存関係と同じ移植性を持つことに注意してください。 たとえば、サードパーティ ライブラリが macOS のみをサポートする場合、アプリを Windows システムに移植することはできません。 この状況は、サードパーティの依存関係自体がネイティブ コードに依存する場合に生じる可能性があります。 この好例は Kestrel サーバーです。 このようなサードパーティの依存関係を含むアプリケーションに対して FDD が作成されると、発行された出力には、ネイティブの依存関係がサポートする (そして、その NuGet パッケージ内に存在する) 各[ランタイム識別子 (RID)](../../rid-catalog.md#what-are-rids) のフォルダーが含まれます。

## <a name="self-contained-deployments-scd"></a>自己完結型の展開 (SCD) ##

自己完結型の展開では、アプリおよびすべてのサードパーティの依存関係だけでなく、アプリのビルドに使用する .NET Core のバージョンも展開します。 ただし、SCD の作成には、さまざまなプラットフォーム上の [.NET Core のネイティブの依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)自体 (たとえば、macOS 上の OpenSSL) は含まれないので、アプリケーションを実行する前にこれらの依存関係をインストールする必要があります。 

### <a name="why-deploy-a-self-contained-deployment"></a>自己完結型の展開を展開する理由 ###

自己完結型の展開を展開するのには、次の 2 つの主な利点があります。

- アプリで展開されている .NET Core のバージョンは、あなただけがコントロールできます。 .NET Core を操作できるのはあなただけです。

- ターゲット システムが実行できる .NET Core のバージョンを提供しているので、ターゲット システムで .NET Core アプリを確実に実行できます。

また、次のいくつかの短所もあります。

- .NET Core が展開パッケージに含まれているので、展開パッケージをビルドするターゲット プラットフォームを事前に選択する必要があります。

- .NET Core だけでなくアプリおよびそのサードパーティの依存関係を含める必要があるので、展開パッケージは比較的大きくなります。

- 多数の自己完結型の .NET Core アプリをシステムに展開すると、各アプリが .NET Core ファイルを複製するので、非常に多くのディスク領域を使用する可能性があります。

### <a name="a-namesimpleselfa-deploying-a-simple-self-contained-deployment"></a><a name="simpleSelf"></a>単純な自己完結型の展開を展開する ###

サードパーティの依存関係を含まない自己完結型の展開を展開するプロセスには、プロジェクトの作成、csproj ファイルの変更、アプリのビルド、テスト、および発行が含まれます。  C# で記述された次の単純な例は、このプロセスを示しています。 この例では、コマンドラインの `dotnet` ユーティリティを使用します。ただし、Visual Studio や Visual Studio Code などの開発環境を使用して、この例をコンパイル、テスト、および発行することもできます。

1. プロジェクトのディレクトリを作成し、コマンドラインから `dotnet new` と入力して、新しい C# コンソール プロジェクトを作成します。

2. エディターで `Program.cs` ファイルを開き、自動生成されたコードを次のコードに置き換えます。 テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。 正規表現 `\w+` を使用して、入力テキストの単語を分離します。

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. `csproj` ファイルで、アプリがターゲットとするプラットフォームを定義する `<RuntimeIdentifiers>` タグを `<PropertyGroup>` セクションの下に作成し、ターゲットとする各プラットフォームのランタイム識別子を指定します。 ランタイム識別子の一覧については、「[Runtime IDentifier catalog](../../rid-catalog.md)」 (ランタイム識別子のカタログ) を参照してください。 たとえば、次の `runtimes` セクションは、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。

    ```xml
        <PropertyGroup>
          <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
        </PropertyGroup>
    ```
なお、RID の分離にはセミコロンを追加する必要があることに注意してください。 また、`<RuntimeIdentifier>` 要素は、`csproj` ファイルの任意の `<PropertyGroup>` に入れることが可能です。 完全なサンプル `csproj` ファイルについては、このセクションの後の部分に示されています。

4. `dotnet restore` コマンドを実行して、プロジェクトで指定された依存関係を復元します。

5. `dotnet build` コマンドを使用して、各ターゲット プラットフォーム上のアプリのデバッグ ビルドを作成します。 ビルドするランタイム識別子を指定しない限り、`dotnet build` コマンドは、現在のシステムのランタイム ID のみのビルドを作成します。 次のコマンドを使用して、両方のターゲット プラットフォームに対してアプリをビルドできます。

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.11-x64
    ```
各プラットフォームのアプリのデバッグ ビルドは、プロジェクトの `.\bin\Debug\netcoreapp1.0\<runtime_identifier>` サブディレクトリ内にあります。

6. プログラムをテストしてデバッグしたら、次のように両方のターゲット プラットフォームに対して `dotnet publish` コマンドを使用して、ターゲット プラットフォームごとにアプリで展開するファイルを作成できます。

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.11-x64
   ```
これにより、各ターゲット プラットフォームに対してアプリのリリース (デバッグではなく) バージョンが作成されます。 作成されたファイルは、プロジェクトの `.\bin\release\netcoreapp1.0\<runtime_identifier>` サブディレクトリのサブディレクトリ内にある、`publish` という名前のサブディレクトリに配置されます。 各サブディレクトリには、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。

7. アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。アプリケーションのファイルと共にパッケージ化しないように選択することもできます。

発行されたファイルは、任意の方法で展開できます。 たとえば、zip ファイル内にパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。 

このプロジェクトの完全な `csproj` ファイルを次に示します。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
    <VersionPrefix>1.0.0</VersionPrefix>
    <DebugType>Portable</DebugType>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Newtonsoft.Json">
      <Version>9.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161102-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```


### <a name="deploying-a-self-contained-deployment-with-third-party-dependencies"></a>サードパーティの依存関係を含む自己完結型の展開を展開する ###

1 つまたは複数のサードパーティの依存関係を含む自己完結型の展開を展開するプロセスには、サードパーティの依存関係の追加が含まれます。

1. 任意のサードパーティ ライブラリへの参照を `csproj` ファイルの `<ItemGroup>` セクションに追加します。 次の `<ItemGroup>` セクションは、サードパーティ ライブラリとして Json.NET を使用します。

    ```xml
      <ItemGroup>
        <PackageReference Include="Microsoft.NETCore.App">
          <Version>1.0.1</Version>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Sdk">
          <Version>1.0.0-alpha-20161102-2</Version>
          <PrivateAssets>All</PrivateAssets>
        </PackageReference>
        <PackageReference Include="Newtonsoft.Json">
          <Version>9.0.1</Version>
        </PackageReference>
      </ItemGroup>
    ```
2. サードパーティの依存関係を含む NuGet パッケージをシステムにまだダウンロードしていない場合は、ダウンロードします。 依存関係をアプリで使用できるようにするには、依存関係を追加してから、`dotnet restore` コマンドを実行します。 発行時に依存関係はローカルの NuGet キャッシュからが解決されるので、システムで使用可能になる必要があります。

このプロジェクトの完全な csproj ファイルを次に示します。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
    <VersionPrefix>1.0.0</VersionPrefix>
    <DebugType>Portable</DebugType>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Newtonsoft.Json">
      <Version>9.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161102-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

アプリケーションを展開すると、アプリで使用されるすべてのサードパーティの依存関係も、アプリケーション ファイルに含まれています。 アプリが実行されているシステム上にサードパーティ ライブラリが既に存在している必要はありません。

サードパーティ ライブラリを含む自己完結型の展開は、そのライブラリでサポートされるプラットフォームにのみ展開できます。 これは、フレームワークに依存する展開でネイティブの依存関係と共にサードパーティの依存関係を含む場合に似ています。 

### <a name="deploying-a-self-contained-deployment-with-a-smaller-footprint"></a>フットプリントがより小さい自己完結型の展開を展開する ###

ターゲット システムで十分な記憶域の可用性が問題になる可能性がある場合は、一部のシステム コンポーネントを除外することで、アプリの全体的なフットプリントを削減できます。 このためには、アプリによって csproj ファイルに含まれる .NET Core コンポーネントを明示的に定義します。

フットプリントがより小さい自己完結型の展開を作成するには、まず次の 2 つの手順に従って自己完結型の展開を作成します。 `dotnet new` コマンドを実行し、C# ソース コードをアプリに追加したら、次の手順を実行します。

1. `csproj` ファイルを開き、`frameworks` セクションを次のコードに置き換えます。

    ```xml
    <PropertyGroup>
      <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  ```
この操作は、`netcoreapp1.0`フレームワーク全体 (.NET Core CLR, .NET Core ライブラリ、およびその他の多数のシステム コンポーネントを含む) を使用する代わりに、アプリが .NET 標準ライブラリのみを使用することを示します。

2. `dependencies` セクションを次のコードに置き換えます。

    ```xml
    <ItemGroup>
      <PackageReference Include="NETSTandard.Library">
        <Version>1.6.0</Version>
      </PackageReference>
      <PackageReference Include="Microsoft.NETCore.Runtime.CoreCLR">
        <Version>1.0.2</Version>
      </PackageReference>
      <PackageReference Include="Microsoft.NETCore.DotNetHostPolicy">
        <Version>1.0.1</Version>
      </PackageReference>
      <PackageReference Include="Microsoft.NET.Sdk">
        <Version>1.0.0-alpha-20161102-2</Version>
        <PrivateAssets>All</PrivateAssets>
      </PackageReference>
    </ItemGroup>
  ```

   これにより、アプリで使用されるシステム コンポーネントが定義されます。 アプリでパッケージ化されたシステム コンポーネントには、.NET 標準ライブラリ、.NET Core ランタイム、および .NET Core ホストが含まれています。 これにより、フットプリントがより小さい自己完結型の展開が生成されます。

3. 「[単純な自己完結型の展開を展開する](#simpleSelf)」で行ったように、`csproj` ファイルの `<PropertyGroup>`に、アプリがターゲットとするプラットフォームを定義する `<RuntimeIdentifiers>` 要素を作成し、ターゲットとする各プラットフォームのランタイム識別子を指定します。 ランタイム識別子の一覧については、「[Runtime IDentifier catalog](../../rid-catalog.md)」 (ランタイム識別子のカタログ) を参照してください。 たとえば、次の例は、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。

    ```xml
        <PropertyGroup>
          <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
        </PropertyGroup>
    ```
    

完全なサンプル `csproj` ファイルについては、このセクションの後の部分に示されています。

4. `dotnet restore` コマンドを実行して、プロジェクトで指定された依存関係を復元します。

5. `dotnet build` コマンドを使用して、各ターゲット プラットフォーム上のアプリのデバッグ ビルドを作成します。 ビルドするランタイム識別子を指定しない限り、`dotnet build` コマンドは、現在のシステムのランタイム ID のみのビルドを作成します。 次のコマンドを使用して、両方のターゲット プラットフォームに対してアプリをビルドできます。

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.11-x64
    ```

6. プログラムをテストしてデバッグしたら、次のように両方のターゲット プラットフォームに対して `dotnet publish` コマンドを使用して、ターゲット プラットフォームごとにアプリで展開するファイルを作成できます。

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.11-x64
   ```
これにより、各ターゲット プラットフォームに対してアプリのリリース (デバッグではなく) バージョンが作成されます。 作成されたファイルは、プロジェクトの `.\bin\release\netstandard1.6\<runtime_identifier>` サブディレクトリのサブディレクトリ内にある、`publish` という名前のサブディレクトリに配置されます。 各サブディレクトリには、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。

7. アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。アプリケーションのファイルと共にパッケージ化しないように選択することもできます。

発行されたファイルは、任意の方法で展開できます。 たとえば、zip ファイル内にパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。 

このプロジェクトの完全な `csproj` ファイルを次に示します。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
    <VersionPrefix>1.0.0</VersionPrefix>
    <DebugType>Portable</DebugType>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>
  <ItemGroup>
    <PackageReference Include="NETSTandard.Library">
      <Version>1.6.0</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NETCore.Runtime.CoreCLR">
      <Version>1.0.2</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NETCore.DotNetHostPolicy">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161102-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```




<!--HONumber=Nov16_HO3-->


