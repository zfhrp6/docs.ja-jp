---
title: ".NET Core アプリケーション展開 | Microsoft Docs"
description: ".NET Core アプリケーションの展開。"
keywords: ".NET, .NET Core, .NET Core 展開"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.translationtype: Human Translation
ms.sourcegitcommit: 3ffe3909902659a22cb25bac6dc5aaa4f5b9fde2
ms.openlocfilehash: 31503e39d8a96092dbce03c17397e1adfec6421e
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---

# <a name="net-core-application-deployment"></a>.NET Core アプリケーションの展開

.NET Core アプリケーションに対して、次の 2 種類の展開を作成できます。

- フレームワークに依存する展開。 名前が示すように、フレームワークに依存する展開 (FDD) は、ターゲット システムに .NET Core のシステム全体の共有バージョンが存在することに依存します。 .NET Core は既に存在するので、アプリは .NET Core のインストール間で移植することもできます。 アプリには、それ自体のコード、および .NET Core ライブラリの外部にあるサードパーティの依存関係のみが含まれています。 FDD には、コマンドラインから [dotnet ユーティリティ](../tools/dotnet.md)を使って起動できる *.dll* ファイルが含まれています。 たとえば、`dotnet app.dll` は `app` という名前のアプリケーションを実行します。

- 自己完結型の展開。 FDD とは異なり、自己完結型の展開 (SCD) は、ターゲット システムに共有コンポーネントが存在することに依存しません。 .NET Core ライブラリと .NET Core ランタイムの両方を含むすべてのコンポーネントがアプリケーションに含まれており、他の .NET Core アプリケーションから分離されています。 SCD には、プラットフォーム固有の .NET Core ホストの名前変更後のバージョンである実行可能ファイル (`app` という名前のアプリケーションに対する Windows プラットフォーム上の *app.exe* など)、および実際のアプリケーションである *.dll* ファイル (*app.dll* など) が含まれています。

## <a name="framework-dependent-deployments-fdd"></a>フレームワークに依存する展開 (FDD)

FDD では、アプリ、およびサードパーティの依存関係のみを展開します。 アプリは、ターゲット システムに存在する .NET Core のバージョンを使うので、.NET Core を展開する必要はありません。 これは、.NET Core アプリの既定の展開モデルです。

### <a name="why-create-a-framework-dependent-deployment"></a>フレームワークに依存する展開を作成する理由

FDD の展開には、次のいくつかの利点があります。

- .NET Core アプリが実行されるターゲットのオペレーティング システムを事前に定義する必要はありません。 .NET Core は、オペレーティング システムに関係なく実行可能ファイルとライブラリに共通の PE ファイル形式を使用するので、.NET Core は、基になるオペレーティング システムに関係なくアプリを実行できます。 PE ファイル形式の詳細については、「[.NET Assembly File Format](../../standard/assembly-format.md)」 (.NET アセンブリのファイル形式) を参照してください。

- 展開パッケージは小サイズです。 .NET Core 自体ではなく、アプリとその依存関係のみを展開します。

- 複数のアプリが、同じ .NET Core インストールを使用します。これにより、ホスト システム上のディスク領域とメモリ使用量の両方が削減されます。

次のいくつかの短所もあります。

- ターゲットとする .NET Core のバージョンまたはそれ以降のバージョンがホスト システムに既にインストールされている場合にのみ、アプリを実行できます。

- 将来のリリースでは、ユーザーの認識なしに .NET Core ランタイムおよびライブラリが変更される場合があります。 まれなケースでは、アプリのビヘイビアーが変更される可能性があります。

## <a name="self-contained-deployments-scd"></a>自己完結型の展開 (SCD)

自己完結型の展開では、アプリおよびすべての必要なサードパーティの依存関係と共に、アプリのビルドに使った .NET Core のバージョンも展開します。 SCD の作成には、さまざまなプラットフォーム上の [.NET Core のネイティブの依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) (たとえば、macOS 上の OpenSSL) は含まれないので、アプリが実行する前にこれらが存在している必要があります。

### <a name="why-deploy-a-self-contained-deployment"></a>自己完結型の展開を展開する理由

自己完結型の展開を展開するのには、次の 2 つの主な利点があります。

- アプリで展開されている .NET Core のバージョンは、あなただけがコントロールできます。 .NET Core を操作できるのはあなただけです。

- ターゲット システムが実行できる .NET Core のバージョンを提供しているので、ターゲット システムで .NET Core アプリを確実に実行できます。

また、次のいくつかの短所もあります。

- .NET Core が展開パッケージに含まれているので、展開パッケージをビルドするターゲット プラットフォームを事前に選択する必要があります。

- .NET Core だけでなくアプリおよびそのサードパーティの依存関係を含める必要があるので、展開パッケージは比較的大きくなります。

- 多数の自己完結型の .NET Core アプリをシステムに展開すると、各アプリが .NET Core ファイルを複製するので、非常に多くのディスク領域を使用する可能性があります。

## <a name="step-by-step-examples"></a>手順の例

CLI ツールで .NET Core アプリを展開する手順の例については、「[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md)」(CLI ツールで .NET Core アプリを展開する) をご覧ください。 Visual Studio で .NET Core アプリを展開する手順の例については、「[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md)」(Visual Studio で .NET Core アプリを展開する) をご覧ください。 各トピックには、次の展開の例が含まれます。

- フレームワークに依存する展開
- サードパーティの依存関係を含む、フレームワークに依存する展開
- 自己完結型の展開
- サードパーティの依存関係を含む、自己完結型の展開

# <a name="see-also"></a>関連項目

[CLI ツールで .NET Core アプリを展開する](deploy-with-cli.md)   
[Visual Studio で .NET Core アプリを展開する](deploy-with-vs.md)   
[パッケージ、メタパッケージ、フレームワーク](../packages.md)   
[.NET Core のランタイム識別子 (RID) のカタログ](../rid-catalog.md)

