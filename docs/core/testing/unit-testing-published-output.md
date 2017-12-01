---
title: "パブリッシュされた出力を dotnet vstest をテストします。"
description: "Dotnet vstest コマンドを使用してパブリッシュされた出力でテストを実行する方法を説明します。"
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>パブリッシュされた出力を dotnet vstest をテストします。

使用して既にパブリッシュされた出力でテストを実行することができます、`dotnet vstest`コマンド。 これは機能 xUnit、MSTest、NUnit にテストします。 単に、パブリッシュされた出力の一部であった DLL ファイルを検索し、実行します。
```
dotnet vstest <MyPublishedTests>.dll
```
ここで`<MyPublishedTests>`発行されたテスト プロジェクトの名前を指定します。

### <a name="example-of-running-tests-on-a-published-dll"></a>パブリッシュされた DLL のテストの実行の例

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] 注: アプリは対象にする framework 以外の場合`netcoreapp`まだ実行することができます、 `dotnet vstest` framework フラグで対象のフレームワークに渡すことによってコマンド。 たとえば、`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"` のようにします。 Visual Studio 2017 更新プログラム 5 には、目的のフレームワークが自動的に検出します。

### <a name="related-topics"></a>関連トピック
- [Dotnet テスト、xUnit で単体テスト](unit-testing-with-dotnet-test.md)
- [Dotnet テストと、MSTest の単体テスト](unit-testing-with-mstest.md)
