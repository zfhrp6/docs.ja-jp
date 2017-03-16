---
title: "MSTest と .NET Core を使用する | Microsoft Docs"
description: "MSTest と .NET Core を使用する方法"
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 02/10/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 4ffc7dd4e11820a3c50ca83847a7ab418bf2faf3
ms.lasthandoff: 03/07/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a>MSTest と .NET Core による単体テスト

## <a name="creating-the-projects"></a>プロジェクトの作成

「[クロス プラットフォーム ツールを使用したライブラリの記述](../tutorials/libraries.md)」に関するページには、ソースとテストの両方に複数のプロジェクトから成るソリューションを構成するための情報が含まれています。 この記事は、この規則に従います。 最終的なプロジェクト構造は、次のようになります。

```
/unit-testing-using-mstest
|__/PrimeService
   |__Source Files
   |__PrimeService.csproj
|__/PrimeService.Tests
   |__Test Files
   |__PrimeService.csproj
```

### <a name="creating-the-source-project"></a>ソース プロジェクトの作成

シェル ウィンドウを開きます。 *unit-testing-using-mstest* ディレクトリで開始し、*PrimeService* ディレクトリを作成します。
*PrimeService* を現在のディレクトリにします。それから `dotnet new classlib` を実行してソース プロジェクトを作成します。

*Class1.cs* の名前を *PrimeService.cs* に変更します。 テスト駆動開発 (TDD) を使用するため、`PrimeService` クラスのエラーが発生する実装を作成します。

```cs
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first");
        } 
    }
}
```

### <a name="creating-the-test-project"></a>テスト プロジェクトの作成

次に、*unit-testing-using-mstest* ディレクトリに戻り、*PrimeServices.Tests* ディレクトリを作成します。
*PrimeService.Tests* ディレクトリを現在のディレクトリにします。それから `dotnet new mstest` を利用して新しいプロジェクトを作成します。 これにより、テスト ライブラリとして MStest を使用するテスト プロジェクトが作成されます。 

生成されたテンプレートで、*PrimeServiceTests.csproj* ファイルのテスト ランナーが構成されました。

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-preview-20170123-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.10-rc2" />
  <PackageReference Include="MSTest.TestFramework" Version="1.0.8-rc2" />
</ItemGroup>
```

テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。
`dotnet new` により、MSTest SDK、MSTest テスト フレームワーク、MSTest ランナーが追加されました。 別の依存関係として PrimeService パッケージをプロジェクトに追加する必要があります。 これは `dotnet` CLI を利用して実行できます。

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

あるいは、*PrimeService.Tests.csproj* ファイルを手動で編集できます。
最初の `<ItemGroup>` ノードの下で直接、ライブラリ プロジェクトを参照する別の `<ItemGroup>` ノードを追加します。

```xml
  <ItemGroup>
    <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
  </ItemGroup>
```

全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。

この初期構造が配置された後、最初のテストを記述することができます。
その最初の単体テストを確認すると、すべてが構成され、機能とテストを追加しても、スムーズに実行されるようになります。

## <a name="creating-the-first-test"></a>最初のテストの作成

ライブラリまたはテストを構築する前に、*PrimeService* ディレクトリと *PrimeService.Tests* ディレクトリの両方で `dotnet restore` を実行する必要があります。 このコマンドにより、各プロジェクトの必要なすべての NuGet パッケージが復元されます。

TDD のアプローチでは、失敗するテストを&1; つ記述することを要求し、それを渡し、プロセスを繰り返します。 ですから、失敗するテストを&1; つ記述しましょう。 *PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。コンテンツは次のようになります。

```cs
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;
        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, $"1 should not be prime");
        }
    }
}
```

`[TestClass]` 属性は、単体テストを含むクラスを表します。 `[TestMethod]` 属性は、単一のテストとしてメソッドを表します。 

このファイルを保存し、`dotnet build` を実行して、テスト プロジェクトを構築します。
`PrimeService` プロジェクトをまだ構築していない場合、ビルド システムがこのことを検出して構築します。これは、テスト プロジェクトの依存関係によるものです。

では、`dotnet test` を実行してコンソールからテストを実行しましょう。
MSTest テスト ランナーには、コンソールからテストを実行するための、プログラムのエントリ ポイントがあります。 `dotnet test` がテスト ランナーを開始し、テストを含むアセンブリを示すテストランナーにコマンド ライン引数を提供します。

テストが失敗します。 実装はまだ作成していません。
このテストを成功させるための、最も簡単なコードを記述します。

```cs
public bool IsPrime(int candidate) 
{
    if(candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

*PrimeService.Tests* ディレクトリで、`dotnet test` をもう一度実行します。 `dotnet test` コマンドは最初に Prime.Services プロジェクトのビルドを実行し、それから PrimeService.Tests プロジェクトのビルドを実行します。 両方のプロジェクトをビルドすると、この単一テストが実行されます。 成功します。

## <a name="adding-more-features"></a>他の機能の追加

テストが成功したので、他のテストも記述してみましょう。
素数に関する、いくつかの単純なケースが他にもあります (0、-1)。 これらは `[TestMethod]` 属性を使用して新しいテストとして追加できますが、すぐに煩雑になります。 一連の類似のテストを記述できるようになる、他の MSTest 属性があります。  `DataTestMethod` は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。
`[DataRow]` 属性を使用して、そのような入力の値を指定することができます。 
 
 新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストするデータ テスト メソッドを 1 つ作成しましょう。

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs#Sample_TestCode "最初のテスト")]

`dotnet test` を実行すると、このテストのうち&2; つが失敗したことがわかります。
サービスを変更することで、失敗したテストを成功させることができます。 メソッドの先頭にある `if` 句を変更する必要があります。

```cs
if(candidate < 2)
```

これで、すべてのテストが合格します。

他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。 間もなく、[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)と[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)により終了します。

これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。
このソリューションは、新しいパッケージとテストの追加がシームレスになり、当面の問題に集中できるように構成しました。 ツールは自動的に実行されます。
