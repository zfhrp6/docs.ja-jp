---
title: "dotnet テストを使用した .NET Core での単体テスト"
description: "dotnet テストを使用した .NET Core での単体テスト"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdcdb812-6f13-4f20-9e90-0c0977937142
translationtype: Human Translation
ms.sourcegitcommit: 5687fc7ded899a478d1972ffea10a1e37d40124b
ms.openlocfilehash: f1f08f550d7484869e67fe705dc789ca5dae8e2f

---

# <a name="unit-testing-in-net-core-using-dotnet-test"></a>dotnet テストを使用した .NET Core での単体テスト

執筆: [Steve Smith](http://ardalis.com) / [Bill Wagner](https://github.com/BillWagner)

[サンプル コードを表示またはダウンロードする](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test)

> [!NOTE]
> このトピックは .NET Core 1.0 を対象としています。

## <a name="creating-the-projects"></a>プロジェクトの作成

「[クロス プラットフォーム ツールを使用したライブラリの記述](../tutorials/libraries.md)」に関するページには、ソースとテストの両方に複数のプロジェクトから成るソリューションを構成するための情報が含まれています。 この記事は、この規則に従います。 最終的なプロジェクト構造は、次のようになります。

```
/unit-testing-using-dotnet-test
|__global.json
|__/src
   |__/PrimeService
      |__Source Files
      |__project.json
|__/test
   |__/PrimeService.Tests
      |__Test Files
      |__project.json
```

ルート ディレクトリに、`src` と `test` のディレクトリの名前を含む `global.json` を作成する必要があります。

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

### <a name="creating-the-source-project"></a>ソース プロジェクトの作成

次に、`src` ディレクトリに `PrimeService` ディレクトリを作成します。
そのディレクトリに移動して、`dotnet new -t lib` を実行してソース プロジェクトを作成します。


`Library.cs` の名前を `PrimeService.cs` に変更します。 テスト駆動開発 (TDD) を使用するため、`PrimeService` クラスのエラーが発生する実装を作成します。

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

次に、'test' ディレクトリに移動し、`PrimeServices.Tests` ディレクトリを作成します。
`PrimeServices.Tests` ディレクトリに移動し、`dotnet new -t xunittest` を使用して新しいプロジェクトを作成します。 `dotnet new -t xunittest` によって、テスト ライブラリとして xunit を使用するテスト プロジェクトが作成されます。 

生成されたテンプレートの、`project.json` のルートにテスト ランナーが構成されています。

```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",
  // ...
}
```

このテンプレートは、`netcoreapp1.0` を使用するフレームワーク ノードも設定します。また、.NET Core RTM で動作するための xUnit.net の取得に必要なインポートが含まれています。

```json
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dotnet54",
        "portable-net45+win8" 
      ]
    }
  }
```

テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。
`dotnet new` によって、xunit と xunit ランナーが追加されています。 別の依存関係として PrimeService パッケージをプロジェクトに追加する必要があります。

```json
"dependencies": {
  "xunit":"2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "PrimeService": {
    "target": "project"
  }
}
```

`PrimeService` プロジェクトにディレクトリ パスの情報が含まれていないことに注目してください。 `src` および `test` の予想される階層と一致するプロジェクト構造を作成しているため、`global.json` ファイルにはビルド システムがプロジェクトの正しい場所を見つけることが示されます。 `"target": "project"` 要素を追加して、NuGet に NuGet フィードではなくプロジェクト ディレクトリを検索するように通知します。 このキーがないと、内部ライブラリと同じ名前のパッケージがダウンロードされる可能性があります。

全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/project.json)で確認できます。

この初期構造が配置された後、最初のテストを記述することができます。
その最初の単体テストを確認すると、すべてが構成され、機能とテストを追加しても、スムーズに実行されるようになります。

## <a name="creating-the-first-test"></a>最初のテストの作成

TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡し、プロセスを繰り返します。 ですから、失敗するテストを 1 つ記述しましょう。 `program.cs` を `PrimeService.Tests` ディレクトリから削除し、次の内容で新しい C# ファイルを作成します。

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
xunit テスト ランナーには、コンソールからテストを実行するための、プログラムのエントリ ポイントがあります。 `dotnet test` がテスト ランナーを開始し、テストを含むアセンブリを示すテストランナーにコマンド ライン引数を提供します。

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
素数に関する、いくつかの単純なケースが他にもあります (0、-1)。 これらは `[Fact]` 属性を使用して新しいテストとして追加できますが、すぐに煩雑になります。 一連の類似のテストを記述できるようになる、他の xunit 属性があります。  `Theory` は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。
`[InlineData]` 属性を使用して、そのような入力の値を指定することができます。 
 
 新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストする単純な理論を作成しましょう。

```cs
[Theory]
[InlineData(-1)]
[InlineData(0)]
[InlineData(1)]
public void ReturnFalseGivenValuesLessThan2(int value)
{
    var result = _primeService.IsPrime(value);

    Assert.False(result, $"{value} should not be prime");
}
```

`dotnet test` を実行すると、このテストのうち 2 つが失敗したことがわかります。
サービスを変更することで、失敗したテストを成功させることができます。 メソッドの先頭にある `if` 句を変更する必要があります。

```cs
if(candidate < 2)
```

これで、すべてのテストが合格します。

他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。 間もなく、[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/test/PrimeService.Tests/PrimeServie_IsPrimeShould.cs)と[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/src/PrimeService/PrimeService.cs)により終了します。

これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。
このソリューションは、新しいパッケージとテストの追加がシームレスになり、当面の問題に集中できるように構成しました。 ツールは自動的に実行されます。
   
   > [!TIP]
   > Windows プラットフォームでは、MSTest を使用できます。 「[Using MSTest on Windows document](./using-mstest-on-windows.md)」(Windows ドキュメントで MSTest を使用する) を参照してください。



<!--HONumber=Jan17_HO3-->


