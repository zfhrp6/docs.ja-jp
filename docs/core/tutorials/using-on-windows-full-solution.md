---
title: Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築
description: Windows 上の Visual Studio 2017 で完全な .NET Core ソリューションを構築する方法を説明します。
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8e37eb578f9c4ac63fbc120e6227098ea69d169d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築

Visual Studio 2017 は、.NET Core アプリケーション開発用の機能をすべて備えた開発環境を提供します。 このドキュメントでは、再利用可能なライブラリ、サードパーティ製ライブラリのテストと使用を含む、一般的な .NET Core ソリューションをビルドするために必要な手順について説明します。 

## <a name="prerequisites"></a>必須コンポーネント

[前提条件のページ](../windows-prerequisites.md)の指示に従って、環境を更新します。

## <a name="a-solution-using-only-net-core-projects"></a>.NET Core プロジェクトのみを使用するソリューション

### <a name="writing-the-library"></a>ライブラリの作成

1. Visual Studio で、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。 **[新しいプロジェクト]** ダイアログで **[Visual C#]** ノードを展開し、**[.NET Standard]** ノードを選択して **[クラス ライブラリ (.NET Standard)]** を選択します。 

2. プロジェクトの名前を "Library" に、ソリューションの名前を "Golden" に設定します。 **[ソリューションのディレクトリを作成]** はオンのままにします。 **[OK]** をクリックします。

3. ソリューション エクスプローラーで **[依存関係]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。

4. **[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。**Newtonsoft.Json** を参照します。 **[インストール]** をクリックして、使用許諾契約に同意します。 これで、**[依存関係] の [NuGet]** にパッケージが表示され、自動的に復元されるようになります。

5. ファイルの名前を `Class1.cs` から `Thing.cs` に変更します。 クラス名の変更をそのまま使用します。 メソッドの追加: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   ソリューションがエラーのない状態でビルドされます。

### <a name="writing-the-test-project"></a>テスト プロジェクトの作成

1. ソリューション エクスプローラーで、**[ソリューション]** ノードのコンテキスト メニューを開き、**[追加]**、**[新しいプロジェクト]** の順に選択します。 **[新しいプロジェクト]** ダイアログ ボックスにある **[Visual C#] の [.NET Core]** で、**[単体テスト プロジェクト (.NET Core)]** を選択します。 "TestLibrary" という名前を付けて [OK] をクリックします。 

2. **TestLibrary** プロジェクトで、**[依存関係]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。 **[プロジェクト]** をクリックし、ライブラリ プロジェクトを確認して [OK] をクリックします。 これで、テスト プロジェクトからライブラリに参照が追加されます。

3. `UnitTest1.cs` ファイルの名前を `LibraryTests.cs` に変更して、クラスの名前変更を承諾します。 ファイルの先頭に `using Library;` を追加し、`TestMethod1` メソッドを次のコードに置き換えます。
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   ソリューションをビルドできるようになります。 
   
4. **[テスト]** メニューで、**[Windows]**、**[テスト エクスプローラー]** の順に選択し、テスト エクスプローラー ウィンドウをワークスペースに取り込みます。 数秒後に、`ThingGetsObjectValFromNumber` テストがテスト エクスプローラーに表示されます。 **[すべて実行]** をクリックします。
   
   テストで問題がないことを確認します。

### <a name="writing-the-console-app"></a>コンソール アプリの作成

1. ソリューション エクスプローラーで、ソリューションのコンテキスト メニューを開き、新しい**コンソール アプリケーション (.NET Core)** プロジェクトを追加します。 それに "App" という名前を付けます。

2. **App** プロジェクトで、**[依存関係]** ノードのコンテキスト メニューを開き、**[追加]**、**[参照]** の順に選択します。 

3. **[参照マネージャー]** ダイアログ ボックスで、**[プロジェクト]**、**[ソリューション]** ノードの **[ライブラリ]** をオンにして、**[OK]** をクリックします。

6. **App** ノードのコンテキスト メニューを開き、**[スタートアップ プロジェクトに設定]** を選択します。 これで、F5 キーまたは Ctrl + F5 キーを押したときにコンソール アプリケーションが起動します。

7. `Program.cs` ファイルを開き、`using Library;` ディレクティブをファイルの先頭に追加して、`Console.WriteLine($"The answer is {new Thing().Get(42)}.");` を `Main` メソッドに追加します。

8. 追加した行の後にブレークポイントを設定します。

9. F5 キーを押してアプリケーションを実行します。

   アプリケーションがエラーのない状態でビルドされ、ブレークポイントがヒットします。 また、アプリケーションが "The answer is 42." と出力することを確認します。
