---
title: "dotnet テストを使用した .NET Core での単体テスト | Microsoft Docs"
description: "dotnet テストを使用した .NET Core での単体テスト"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 002/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: cd860241f5f20b6a4f1ccfec60e0c9cd5079152a
ms.lasthandoff: 03/07/2017

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>dotnet テストを使用した .NET Core での単体テスト

執筆: [Steve Smith](http://ardalis.com) / [Bill Wagner](https://github.com/BillWagner)

[サンプル コードを表示またはダウンロードする](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

## <a name="creating-the-projects"></a>プロジェクトの作成

「[クロス プラットフォーム ツールを使用したライブラリの記述](../tutorials/libraries.md)」に関するページには、ソースとテストの両方に複数のプロジェクトから成るソリューションを構成するための情報が含まれています。 この記事は、この規則に従います。 最終的なプロジェクト構造は、次のようになります。

```
/unit-testing-using-dotnet-test
|__/PrimeService
   |__Source Files
   |__PrimeService.csproj
|__/PrimeService.Tests
   |__Test Files
   |__PrimeService.csproj
```

### <a name="creating-the-source-project"></a>ソース プロジェクトの作成

`unit-testing-using-dotnet-test` ディレクトリで開始し、`PrimeService` ディレクトリを作成します。
そのディレクトリに移動して、`dotnet new classib` を実行してソース プロジェクトを作成します。


`Class1.cs` の名前を `PrimeService.cs` に変更します。 テスト駆動開発 (TDD) を使用するため、`PrimeService` クラスのエラーが発生する実装を作成します。

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

次に 'unit-testing-using-dotnet-test' ディレクトリに戻り、`PrimeServices.Tests` ディレクトリを作成します。
`PrimeService.Tests` ディレクトリに移動し、`dotnet new xunit` を使用して新しいプロジェクトを作成します。 `dotnet xunit` によって、テスト ライブラリとして xUnit を使用するテスト プロジェクトが作成されます。 

生成されたテンプレートで、PrimeServiceTests.csproj のテスト ランナーが構成されました。

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-preview-20170125-04" />
    <PackageReference Include="xunit" Version="2.2.0-beta5-build3474" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-beta5-build1225" />
  </ItemGroup>
```

テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。
`dotnet new` によって、xUnit と xUnit ランナーが追加されています。 別の依存関係として PrimeService パッケージをプロジェクトに追加する必要があります。 これは `dotnet` CLI を利用して実行できます。

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

または、`PrimeService.Tests.csproj` ファイルを直接編集できます。
最初の `<ItemGroup>` ノードの下で直接、ライブラリ プロジェクトを参照する別の `<ItemGroup>` ノードを追加します。

```xml
  <ItemGroup>
    <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
  </ItemGroup>
```

全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。

この初期構造が配置された後、最初のテストを記述することができます。
その最初の単体テストを確認すると、すべてが構成され、機能とテストを追加しても、スムーズに実行されるようになります。

## <a name="creating-the-first-test"></a>最初のテストの作成

ライブラリまたはテストを構築する前に、`PrimeService` ディレクトリと `PrimeService.Tests` ディレクトリの両方で `dotnet restore` を実行する必要があります。 このコマンドにより、各プロジェクトの必要なすべての NuGet パッケージが復元されます。

TDD のアプローチでは、失敗するテストを&1; つ記述することを要求し、それを渡し、プロセスを繰り返します。 ですから、失敗するテストを&1; つ記述しましょう。 `UnitTest1.cs` を `PrimeService.Tests` ディレクトリから削除し、次の内容で `PrimeService_IsPrimeShould.cs` という名前の新しい C# ファイルを作成します。

```cs
namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;
         public PrimeService_IsPrimeShould()
         {
             _primeService = new PrimeService();
         }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

`[Fact]` 属性は、単一のテストとしてメソッドを表します。 

このファイルを保存し、`dotnet build` を実行して、テスト プロジェクトを構築します。
`PrimeService` プロジェクトをまだ構築していない場合、ビルド システムがこのことを検出して構築します。これは、テスト プロジェクトの依存関係によるものです。

では、`dotnet test` を実行してコンソールからテストを実行しましょう。
xUnit テスト ランナーには、コンソールからテストを実行するための、プログラムのエントリ ポイントがあります。 `dotnet test` がテスト ランナーを開始し、テストを含むアセンブリを示すテストランナーにコマンド ライン引数を提供します。

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

### <a name="adding-more-features"></a>他の機能の追加

テストが成功したので、他のテストも記述してみましょう。
素数に関する、いくつかの単純なケースが他にもあります (0、-1)。 これらは `[Fact]` 属性を使用して新しいテストとして追加できますが、すぐに煩雑になります。 一連の類似のテストを記述できるようになる、他の xUnit 属性があります。  `Theory` は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。
`[InlineData]` 属性を使用して、そのような入力の値を指定することができます。 
 
 新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストする単純な理論を作成しましょう。

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs#Sample_TestCode "最初のテスト")]
```

Run `dotnet test` and you'll see that two of these tests fail.
You can make them pass by changing the service. You need to change
the `if` clause at the beginning of the method:

```cs
if(candidate < 2)
```

これで、すべてのテストが合格します。

他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。 間もなく、[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)と[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs)により終了します。

これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。
このソリューションは、新しいパッケージとテストの追加がシームレスになり、当面の問題に集中できるように構成しました。 ツールは自動的に実行されます。

