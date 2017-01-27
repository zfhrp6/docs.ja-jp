---
title: "Windows での .NET Core の概要"
description: "Visual Studio 2015 を使用した Windows での .NET Core の概要"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 54da8aebd64e86c064214074bc261f72c3b0aedc
ms.openlocfilehash: bf7bf944ebbf3c53ee6206f86e1a168111b54378

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2015"></a>Visual Studio 2015 を使用した Windows での .NET Core の概要

著者: [Bertrand Le Roy](https://github.com/bleroy)、[Phillip Carter](https://github.com/cartermp)

Visual Studio 2015 は、.NET Core アプリケーション開発用の機能をすべて備えた開発環境を提供します。 このドキュメントでは、一般的な .NET Core ソリューションまたは .NET Core コンポーネントを含むソリューションを Visual Studio を使用して構築するために必要な手順について説明します。 シナリオには、.NET Core の最新バージョン対応として明示的にビルドされていないサードパーティ製ライブラリのテストと使用が含まれます。 

## <a name="prerequisites"></a>必須コンポーネント

[前提条件のページ](../windows-prerequisites.md)の指示に従って、環境を更新します。

## <a name="getting-started"></a>作業の開始

次の手順では、.NET Core 開発用に Visual Studio 2015 を設定します。

1. Visual Studio を開き、**[ファイル]** メニューで **[新規作成]**、**[プロジェクト]** の順に選択します。

2. **[新しいプロジェクト]** ダイアログの **[テンプレート]** の一覧で、**[Visual C#]** ノードを展開し、**[.NET Core]** を選択します。 **クラス ライブラリ (.NET Core)** 用、**コンソール アプリケーション (.NET Core)** 用、**ASP.NET Core Web アプリケーション (.NET Core)** 用の 3 つの新しいプロジェクト テンプレートが表示されます。

<a name="a-solution-using-only-net-core-projects"></a>.NET Core プロジェクトのみを使用するソリューション
----------------------------------------

### <a name="writing-the-library"></a>ライブラリの作成

1. Visual Studio で、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順に選択します。 **[新しいプロジェクト]** ダイアログで **[Visual C#]** ノードを展開し、**[.NET Core]** ノードを選択して、**[クラス ライブラリ (.NET Core)]** を選択します。 

2. プロジェクトの名前を "Library" に、ソリューションの名前を "Golden" に設定します。 **[ソリューションのディレクトリを作成]** はオンのままにします。 **[OK]** をクリックします。

3. ソリューション エクスプローラーで **[参照]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。

4. **[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。 **Newtonsoft.Json** を参照します。 **[インストール]** をクリックします。 

5. **[参照]** ノードのコンテキスト メニューを開き、**[パッケージの復元]** を選択します。

6. ファイルの名前を `Class1.cs` から `Thing.cs` に変更します。 クラス名の変更をそのまま使用します。 コンストラクターを削除し、メソッドを追加します。`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。

   ソリューションがエラーのない状態でビルドされます。

### <a name="writing-the-test-project"></a>テスト プロジェクトの作成

1. ソリューション エクスプローラーで、**[ソリューション]** ノードのコンテキスト メニューを開き、**[追加]**、**[新しいソリューション フォルダー]** の順に選択します。 フォルダーの名前を "test" にします。 
   これはソリューション フォルダーであり、物理フォルダーではありません。

2. **test** フォルダーのコンテキスト メニューを開き、**[追加]** の **[新しいプロジェクト]** を選択します。 **[新しいプロジェクト]** ダイアログ ボックスで、**[コンソール アプリケーション (.NET Core)]** を選択します。 "TestLibrary" という名前を付けて、`Golden\test` パスの下に置きます。 

> [!IMPORTANT]
> クラス ライブラリではなくコンソール アプリケーションのプロジェクトを作成する必要があります。

3. **TestLibrary** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。 

4. **[参照マネージャー]** ダイアログ ボックスで、**[プロジェクト]**、**[ソリューション]** ノードの **[ライブラリ]** をオンにして、**[OK]** をクリックします。 

5. **TestLibrary** プロジェクトで `project.json` ファイルを開き、`"Library": "1.0.0-*"` を `"Library": {"target": "project", "version": "1.0.0-*"}` に置き換えます。 

   これは、`Library` プロジェクトが同じ名前の NuGet パッケージに解決されるのを防ぐためです。 target を "project" に明示的に設定することで、ツールはパッケージではなくその名前のプロジェクトを最初に検索します。 
   
6. **TestLibrary** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[パッケージの復元]** を選択します。

7. **[参照]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。

8. **[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。 **[プレリリースを含める]** チェック ボックスをオンにし、**xUnit** のバージョン 2.2.0 以降を参照して、**[インストール]** をクリックします。 

9. **dotnet-test-xunit** バージョン 2.2.0 以降を参照して、**[インストール]** をクリックします。

10. `project.json` を編集して、`"imports": "dnxcore50"` を `"imports": [ "dnxcore50", "portable-net45+win8" ]` に置き換えます。 

   これにより、xunit ライブラリを正しく復元し、プロジェクトで使用できるようになります。これらのライブラリは、"portable-net45+win8" を含むポータブル プロファイルで使用されるようにコンパイルされていますが、作成された時点では存在しなかった .NET Core は含まれません。 `import` は、ビルド時のツールのバージョン チェックを緩くします。 エラーなしでパッケージを復元できるようになります。

11. `project.json` を編集し、`"frameworks"` セクションの後に `"testRunner": "xunit",` を追加します。

12. `LibraryTests.cs` クラス ファイルを **TestLibrary** プロジェクトに追加し、`using` ディレクティブの `using Xunit;` と `using Library;` をファイルの先頭に追加して、次のコードをクラスに追加します。
    ```csharp
    [Fact]
    public void ThingGetsObjectValFromNumber() {
        Assert.Equal(42, new Thing().Get(42));
    }
    ```
    * 必要に応じて、`Program.cs` ファイルを **TestLibrary** プロジェクトから削除し、`"buildOptions": {"emitEntryPoint": true},` を `project.json` から削除します。

   ソリューションをビルドできるようになります。 
   
13. **[テスト]** メニューで **[Windows]**、**[テスト エクスプローラー]** の順に選択し、テスト エクスプローラーで **[すべて実行]** を選択します。
   
   テストで問題がないことを確認します。

### <a name="writing-the-console-app"></a>コンソール アプリの作成

1. ソリューション エクスプローラーで `src` フォルダーのコンテキスト メニューを開き、新しい**コンソール アプリケーション (.NET Core)** プロジェクトを追加します。 名前を "App" にして、場所を `Golden\src` に設定します。

2. **App** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[追加]**、**[参照]** の順に選択します。 

3. **[参照マネージャー]** ダイアログ ボックスで、**[プロジェクト]**、**[ソリューション]** ノードの **[ライブラリ]** をオンにして、**[OK]** をクリックします。

4. **App** プロジェクトで `project.json` ファイルを開き、`"Library": "1.0.0-*"` を `"Library": {"target": "project"}` に置き換えます。

5. **[参照]** ノードのコンテキスト メニューを開き、**[パッケージの復元]** を選択します。

6. **App** ノードのコンテキスト メニューを開き、**[スタートアップ プロジェクトに設定]** を選択します。

7. `Program.cs` ファイルを開き、`using Library;` ディレクティブをファイルの先頭に追加して、`Console.WriteLine($"The answer is {new Thing().Get(42)}");` を `Main` メソッドに追加します。

8. 追加した行の後にブレークポイントを設定します。

9. F5 キーを押してアプリケーションを実行します。

   アプリケーションがエラーのない状態でビルドされ、ブレークポイントがヒットします。 また、アプリケーションが "The answer is 42." と出力することを確認します。

<a name="a-mixed-net-core-library-and-net-framework-application"></a>.NET Core ライブラリと .NET Framework が混在するアプリケーション
--------------------------------------------------------

前のスクリプトで得られたソリューションから開始し、次の手順を実行します。

1. ソリューション エクスプローラーで **Library** プロジェクトの `project.json` ファイルを開き、`"frameworks": {
    "netstandard1.6" }` を `"frameworks": {
    "netstandard1.4" }` に置き換えます。

2. **Library** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[パッケージの復元]** を選択します。

   ソリューションのビルドと機能は以前とまったく同じです。テストは成功し、コンソール アプリケーションが実行してデバッグできるようになります。

3. **Library** プロジェクトでコンテキスト メニューを開き、**[ビルド]** を選択します。

4. ソリューション エクスプローラーで ** フォルダーのコンテキスト メニューを開き、`src`[追加]** の **[新しいプロジェクト]** を選択します。

5. **[新しいプロジェクト]** ダイアログ ボックスで、**[Visual C#]** ノードを選択し、**[コンソール アプリケーション]** を選択します。

> [!IMPORTANT]
> .NET Core バージョンではなく、標準コンソール アプリケーションを選択します。 このセクションでは、.NET Framework アプリケーションのライブラリを使用します。

6. プロジェクトに "FxApp" という名前を設定し、場所を `Golden\src` に設定します。

7. **FxApp** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。

8. **[参照マネージャー]** ダイアログ ボックスで、**[参照]** を選択してビルドした `Library.dll` の場所を参照し (..Golden\src\Library\bin\Debug\netstandard1.4 パスの下)、**[追加]** をクリックします。 

   .NET Framework から .NET Core コードを参照するもう 1 つの方法としては、ライブラリをパッケージ化し、パッケージを参照することもできます。

9. **[参照]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。

10. **[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。 **[プレリリースを含める]** チェック ボックスをオンにして、**Newtonsoft.Json** を参照します。 **[インストール]** をクリックします。 

11. **FxApp** プロジェクトで `Program.cs` ファイルを開き、`using Library;` ディレクティブをファイルの先頭に追加して、`Console.WriteLine($"The answer is {new Thing().Get(42)}.");` をプログラムの `Main` メソッドに追加します。

12. 追加した行の後にブレークポイントを設定します。

13. **FxApp** をソリューションのスタートアップ アプリケーションにします。

14. F5 キーを押してアプリを実行します。

   アプリケーションがビルドされ、ブレークポイントにヒットします。 アプリケーションから "The answer is 42." と出力されます。
   
   > [!TIP]
   > Windows プラットフォームでは、MSTest を使用できます。 「[Using MSTest on Windows document](../testing/using-mstest-on-windows.md)」(Windows ドキュメントで MSTest を使用する) を参照してください。

<a name="moving-a-library-from-netstandard-14-to-13"></a>netstandard 1.4 から 1.3 へのライブラリの移動
--------------------------------------------

1. ソリューション エクスプローラーで、**Library** プロジェクトの `project.json` ファイルを開きます。

2. `frameworks": { "netstandard1.4" }` を `frameworks": { "netstandard1.3" }` に置き換えます。

3. **Library** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[パッケージの復元]** を選択します。

4. **[ビルド]** メニューの **[Library のビルド]** を選択します。

5. **FxApp** から `Library` の参照を削除した後、..Golden\src\Library\bin\Debug\netstandard1.3 パスを使用して再び追加します。 これにより、バージョン 1.3 を参照するようになります。

6. F5 キーを押してアプリケーションを実行します。

   以前と同じようにすべて動作するはずです。 アプリケーションの出力が "The answer is 42." であり、ブレークポイントにヒットし、変数を調べられることを確認します。

<a name="a-mixed-pcl-library-and-net-framework-application"></a>PCL ライブラリと .NET Framework が混在するアプリケーション
--------------------------------------------------

開いていた場合は前のソリューションを閉じます。ここからは新しいスクリプトを開始します。

### <a name="writing-the-library"></a>ライブラリの作成

1. Visual Studio で、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順に選択します。 **[新しいプロジェクト]** ダイアログで **[Visual C#]** ノードを展開し、**[クラス ライブラリ (iOS、Android、Windows のポータブル)]** を選択します。 

2. プロジェクトの名前を "PCLLibrary" に、ソリューションの名前を "GoldenPCL" に設定します。 **[ソリューションのディレクトリを作成]** はオンのままにします。 **[OK]** をクリックします。

3. ソリューション エクスプローラーで **[参照]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。

4. **[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。 **[プレリリースを含める]** チェック ボックスをオンにして、**Newtonsoft.Json** を参照します。 **[インストール]**をクリックします。 

5. クラスの名前を "Thing" に変更し、メソッドを追加します。`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

6. **[ビルド]** メニューの **[ソリューションのビルド]** を選択、ソリューションがビルドされることを確認します。

### <a name="writing-the-console-app"></a>コンソール アプリの作成

1. ソリューション エクスプローラーで、**[ソリューション 'GoldenPCL']** ノードのコンテキスト メニューを開き、**[追加]** の **[新しいプロジェクト]** を選択します。 **[新しいプロジェクト]** ダイアログ ボックスで、**[Visual C#]** ノードを展開し、**[コンソール アプリケーション]** を選択して、プロジェクトの名前を "App" に設定します。 

2. **App** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[追加]**、**[参照]** の順に選択します。 

3. **[参照マネージャー]** ダイアログ ボックスで、**[参照]** を選択してビルドした `PCLLibrary.dll` の場所を参照し (..\GoldenPCL\PCLLibrary\bin\Debug パスの下)、**[追加]** をクリックします。 

4. **App** プロジェクトで `Program.cs` ファイルを開き、`using PCLLibrary;` ディレクティブをファイルの先頭に追加して、`Console.WriteLine($"The answer is {new Thing().Get(42)}.");` をプログラムの `Main` メソッドに追加します。

5. 追加した行の後にブレークポイントを設定します。

6. ソリューション エクスプローラーで、**App** ノードのコンテキスト メニューを開き、**[スタートアップ プロジェクトに設定]** を選択します。

7. F5 キーを押してアプリを実行します。

   アプリケーションがビルドされて実行し、"The answer is 42." と出力した後でブレークポイントにヒットします。

<a name="moving-a-pcl-to-a-netstandard-library"></a>PCL を NetStandard ライブラリに移動
-------------------------------------
ポータブル クラス ライブラリ ツールは、.NET Standard を対象とするように PCL を自動的に変更できます。 

1.  [プロパティ] ノードをダブルクリックして、プロジェクトのプロパティ ページを開きます

2.  「Targeting header」 (対象ヘッダー) で、「Target .NET Platform Standard」 (対象 .NET Platform Standard) ハイパーリンクをクリックします

3.  確認を求められたら [はい] をクリックします

もともと PCL の対象になっていたすべての対象を含む .NET Standard のバージョンを、ツールが自動的に選択します。 プロジェクト プロパティ ページの [.NET Standard] ドロップダウンを使用して、別のバージョンの .NET Standard を対象にできます。
 
* 前に packages.config があった場合は、変換の前にインストールされているすべてのパッケージのアンインストールを求められる場合があります。

### <a name="manually-edit-projectjson-to-target-net-standard-from-an-existing-portable-class-library"></a>既存のポータブル クラス ライブラリから .NET Standard を対象にするように project.json を手動で編集する

1.  project.json の "supports" 要素に "dnxcore50" が含まれる場合は、それを削除します。

2.  "Microsoft.NETCore" に対する依存関係を削除します

3.  依存する "Microsoft.NETCore.Portable.Compatibility" のバージョンを "1.0.0" から "1.0.1" に変更します

4.  "NETStandard.Library" のバージョン "1.6.0" に対する依存関係を追加します

5.  "frameworks" 要素から "dotnet" フレームワーク (およびその中の "imports" 要素) を削除します

6.  ` "netstandard1.x” : { } ` を frameworks 要素に追加します。x は、対象にする .NET Standard のバージョンに置き換えます

### <a name="example-projectjson"></a>project.json の例

この project.json は、UWP と .NET 4.6 の supports 句を含み、netstandard1.3 を対象にしています。
```
{
  "supports": {
    "net46.app": {},
    "uwp.10.0.app": {},
  },
  "dependencies": {
    "NETStandard.Library": "1.6.0",
    "Microsoft.NETCore.Portable.Compatibility": "1.0.1"
  },
  "frameworks": {
    "netstandard1.3" : {}
  }
}
```





<!--HONumber=Nov16_HO3-->


