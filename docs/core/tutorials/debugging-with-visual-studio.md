---
title: "Visual Studio 2017 での C# Hello World アプリケーションのデバッグ"
description: "Visual Studio 2017 を使用して C# で記述された Hello World アプリをデバッグする方法を説明します。"
keywords: ".NET Core, .NET Core コンソール アプリケーション, .NET Core デバッグ"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
ms.openlocfilehash: 6fbebf69b2772b4159841d13068e7b95a39bea92
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 での Hello World アプリケーションのデバッグ

ここまでは、[「Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築」](.\with-visual-studio.md) または[「Visual Studio 2017 での .NET Core を使用した Visual Basic Hello World アプリケーションの構築」](vb-with-visual-studio.md)の手順に従って、簡単なコンソール アプリケーションを作成して実行しました。 アプリケーションを記述してコンパイルしたら、テストを開始できます。 Visual Studio には、アプリケーションのテストおよびトラブルシューティングの際に使用できるデバッグ ツールの包括的なセットが含まれています。

## <a name="debugging-in-debug-mode"></a>デバッグ モードでのデバッグ

"*デバッグ*" と "*リリース*" は、 Visual Studio に 2 つある既定のビルド構成です。 現時点のビルド構成はツールバーに表示されています。 次のツール バーの画像では、**デバッグ** モードでアプリケーションをコンパイルするように Visual Studio が構成されています。

   ![Visual Studio ツール バー](./media/debugging-with-visual-studio/toolbar1.png)

最初は常にデバッグ モードでプログラムをテストする必要があります。 デバッグ モードでは、コンパイラのほとんどの最適化がオフになり、ビルド プロセスの間に豊富な情報が提供されます。

## <a name="setting-a-breakpoint"></a>ブレークポイントの設定

プログラムをデバッグ モードで実行して、デバッグ機能をいくつか試してみます。

1. "*ブレークポイント*" が設定された行が実行される "*前*" に、アプリケーションの実行が一時的に中断されます。 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
   `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` という行にブレークポイントを設定します。そのためには、コード ウィンドウでこの行の左端の余白をクリックするか、またはこの行を選択してメニューから **[デバッグ]** > **[ブレークポイントの設定/解除]** の順に選びます。 次の図のとおり、Visual Studio ではブレークポイントを強調表示し、左端の余白に赤い円を表示することで、ブレークポイントがある行を示しています。

   ![ブレークポイントが設定された Visual Studio のプログラム ウィンドウ](./media/debugging-with-visual-studio/setbreakpoint.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
   `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` という行にブレークポイントを設定します。そのためには、コード ウィンドウでこの行の左端の余白をクリックするか、またはこの行を選択してメニューから **[デバッグ]** > **[ブレークポイントの設定/解除]** の順に選びます。 次の図のとおり、Visual Studio ではブレークポイントを強調表示し、左端の余白に赤い円を表示することで、ブレークポイントがある行を示しています。

   <a name="visual-studio-program-window-with-breakpoint-setmediadebugging-with-visual-studiovb-setbreakpointpng"></a>![ブレークポイントが設定された Visual Studio のプログラム ウィンドウ](./media/debugging-with-visual-studio/vb-setbreakpoint.png)
---

1. ツール バーで緑色の矢印が付いた **HelloWorld** ボタンを選ぶか、F5 キーを押すか、**[デバッグ]** > **[デバッグの開始]** の順に選ぶことにより、プログラムをデバッグ モードで実行します。

1. プログラムが名前の入力を求めたら、コンソール ウィンドウに文字列を入力して、Enter を押します。

1. プログラムがブレークポイントに到達すると、プログラム実行は停止します。`Console.WriteLine` メソッドが実行される前にも停止します。 **[自動変数]** ウィンドウには、現在の行の付近で使用されている変数の値が表示されます。 **[ローカル]** ウィンドウ (**[ローカル]** タブをクリックすることで表示できる) には、現在実行しているメソッドで定義されている変数の値が表示されます。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
   ![Visual Studio のアプリケーション ウィンドウ](./media/debugging-with-visual-studio/break.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
   <a name="visual-studio-application-windowmediadebugging-with-visual-studiovb-breakpng"></a>![Visual Studio のアプリケーション ウィンドウ](./media/debugging-with-visual-studio/vb-break.png)
---

1. 変数の値を変更して、プログラムにどのような影響があるかを確認できます。 **[イミディエイト ウィンドウ]** が表示されない場合は、**[デバッグ]** > **[Windows]** > **[イミディエイト]** メニュー項目の順に選びます。 **[イミディエイト ウィンドウ]** では、デバッグ中のアプリケーションと対話できます。

1. 変数の値をインタラクティブに変更することもできます。 **[イミディエイト ウィンドウ]** に「`name = "Gracie"`」と入力して、Enter キーを押します。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. **[イミディエイト ウィンドウ]** に「`date = new DateTime(2016,11,01,11,59,00)`」と入力して、Enter キーを押します。

   **[イミディエイト ウィンドウ]** に、文字列変数の値と、<xref:System.DateTime> 値のプロパティが表示されます。 さらに、変数の値は **[自動変数]** ウィンドウおよび **[ローカル]** ウィンドウで更新されます。

   ![[自動変数] ウィンドウと [イミディエイト ウィンドウ]](./media/debugging-with-visual-studio/autosimmediate.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. **[イミディエイト ウィンドウ]** に「`currentDate = new DateTime(2016,11,01,11,59,00)`」と入力して、Enter キーを押します。

<!-- The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value. In addition, the value of the variables is updated in the **Autos** and **Locals** windows.

   ![Autos window and Immediate Window](./media/debugging-with-visual-studio/vb-autosimmediate.png)
-->
---

1. ツール バーの **[続行]** ボタンを選ぶか、**[デバッグ]** > **[続行]** メニュー項目を選んで、プログラムの実行を続けます。 コンソール ウィンドウに表示される値は、**[イミディエイト ウィンドウ]** で行った変更に対応しています。

   !["What is your name?" というプロンプトに対して入力した値 "Jack" と、"Hello Gracie on 11/1/2016 at 11:59am" が表示されたコンソール ウィンドウ](./media/debugging-with-visual-studio/changed.png)

1. 任意のキーを押してアプリケーションを終了して、デバッグ モードを終了します。

## <a name="setting-a-conditional-breakpoint"></a>条件付きブレークポイントの設定

プログラムは、ユーザーが入力した文字列を表示します。 ユーザーが何も入力しないとどうなるでしょうか。 これは、便利なデバッグ機能 "*条件付きブレークポイント*" を使ってテストできます。この機能は、1 つまたは複数の条件が満たされたときにプログラムの実行をブレークします。

条件付きブレークポイントを設定して、ユーザーが文字列の入力に失敗したときに何が起こるかをテストするには、次の手順に従います。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. ブレークポイントを表す赤丸を右クリックします。 コンテキスト メニューの **[条件]** を選んで、**[ブレークポイント設定]** ダイアログを開きます。 **[条件]** チェック ボックスをオンにします。

   ![[ブレークポイント設定] パネル](./media/debugging-with-visual-studio/breakpointsettings.png)

1. **[条件式]** で、[例 x == 5] を次のように置き換えます。

   ```csharp
   String.IsNullOrEmpty(name)
   ```
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. ブレークポイントを表す赤丸を右クリックします。 コンテキスト メニューの **[条件]** を選んで、**[ブレークポイント設定]** ダイアログを開きます。 **[条件]** チェック ボックスをオンにします。

   ![[ブレークポイント設定] パネル](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. **[条件式]** で、[例 x == 5] を次のように置き換えます。

   ```vb
   String.IsNullOrEmpty(name)
   ```
---

   *name* に値が割り当てられていないため、またはその値が空の文字列 ("") であるために `String.IsNullOrEmpty(name)` メソッドは `true` になるという、コード条件を検証します。 "*ヒット カウント*" または "*フィルター条件*" を指定することもできます。ヒット カウントは、ステートメントが指定した回数だけ実行される前にプログラム実行に割り込み、フィルター条件はスレッド識別子、プロセス名、スレッド名などの属性に基づいてプログラム実行に割り込みます。

1. **[閉じる]** を選んでダイアログを閉じます。

1. プログラムをデバッグ モードで実行します。

1. コンソール ウィンドウで、名前の入力を求められたら、Enter キーを押します。

1. `name` が `null` または <xref:System.String.Empty?displayProperty=nameWithType> のどちらかであるという指定した条件が満たされたため、ブレークポイントに到達すると、`Console.WriteLine` メソッドが実行される前に、プログラムの実行が停止します。

1. **[ローカル]** ウィンドウを選ぶと、現在実行しているメソッドのローカル変数の値が表示されます。この場合は、プログラムの `Main` メソッドです。 `name` 変数の値が `""` または <xref:System.String.Empty?displayProperty=nameWithType> であることを調べます。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. **[イミディエイト ウィンドウ]** に次のステートメントを入力して、値が空の文字列であることを確認します。 結果は `true` になります。

   ```csharp
   ? name == String.Empty
   ```

   ![ステートメントが実行された後で値 true を返す [イミディエイト ウィンドウ]](./media/debugging-with-visual-studio/emptystring.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. **[イミディエイト ウィンドウ]** に次のステートメントを入力して、値が空の文字列であることを確認します。 結果は `true` になります。

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![ステートメントが実行された後で値 true を返す [イミディエイト ウィンドウ]](./media/debugging-with-visual-studio/vb-emptystring.png)
---

1. ツール バーの **[続行]** を選んで、プログラムの実行を続けます。

1. 任意のキーを押してコンソール ウィンドウを閉じ、デバッグ モードを終了します。

1. コード ウィンドウの左端の余白のドットをクリックするか、行を選択して **[デバッグ] > [ブレークポイントの設定/解除]** メニュー項目を選んで、ブレークポイントをクリアします。

---
## <a name="stepping-through-a-program"></a>プログラムのステップ実行

Visual Studio では、1 行ずつプログラムをステップ実行して、実行を監視することもできます。 通常は、ブレークポイントを設定してこの機能を使用し、プログラム コードのごく一部を通じてプログラム フローに従います。 プログラムが小さいため、次の手順に従ってプログラム全体をステップ実行できます。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. メニュー バーで **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 次に実行される行が強調表示されて、横に矢印が表示されます。

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/stepinto1.png)

   この時点で **[自動変数]** ウィンドウには、このプログラムで変数が 1 つ (`args`) しか定義されていないことが示されています。 プログラムにコマンド ライン引数を 1 つも渡していないので、値は空の文字列配列になっています。 さらに、空のコンソール ウィンドウが開かれています。

1. **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 次に実行される行が強調表示されます。 図に示すように、直前のステートメントとこのステートメントの間のコードを実行するのにかかった時間は 1 ミリ秒未満です。 宣言された変数はまだ `args` しかなく、コンソール ウィンドウも空のままです。

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/stepinto2.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. メニュー バーで **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 次に実行される行が強調表示されて、横に矢印が表示されます。

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/vb-stepinto1.png)

   この時点で、プログラムにコマンドライン引数をまだ渡していないので、**[自動変数]**ウィンドウには、`args` 変数の値が空の文字列配列である旨が表示されます。 さらに、空のコンソール ウィンドウが開かれています。

1. **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 次に実行される行が強調表示されます。 図に示すように、直前のステートメントとこのステートメントの間のコードを実行するのにかかった時間は 1 ミリ秒未満です。 宣言された変数はまだ `args` しかなく、コンソール ウィンドウも空のままです。

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/vb-stepinto2.png)
---

1. **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 `name` の変数代入を含むステートメントが強調表示されます。 **[自動変数]** ウィンドウに `name` が `null` (C# の場合) または `Nothing` (Visual Basic の場合) であると表示され、コンソール ウィンドウに "What is your name?" という文字列が表示されます。

1. このプロンプトが表示されたら、コンソール ウィンドウに文字列を入力して Enter キーを押します。 コンソールは応答しなくなり、入力した文字列はコンソール ウィンドウに表示されませんが、それでも <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドにより入力はキャプチャされます。

1. **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 `date` (C#) または `currentDate` (Visual Basic) の変数代入を含むステートメントが強調表示されます。 **[自動変数]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値および <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドの呼び出しによって返された値が表示されます。 コンソール ウィンドウには、コンソールにより求められて入力した文字列も表示されます。

1. **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 **[自動変数]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティから代入された後の `date` 変数の値が表示されます。 コンソール ウィンドウに変更はありません。

1. **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。 Visual Studio は、<xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> メソッドを呼び出します。 `date` の値 (または `currentDate`) と `name` の値が **[自動変数]** ウィンドウに表示され、コンソール ウィンドウに書式付き文字列が表示されます。

1. **[デバッグ]** > **[ステップ アウト]** の順に選ぶか、Shift + F11 キーを押します。 これによりステップ バイ ステップの実行が停止します。 コンソール ウィンドウにメッセージが表示され、任意のキーを押すよう求められます。

1. 任意のキーを押してコンソール ウィンドウを閉じ、デバッグ モードを終了します。

## <a name="building-a-release-version"></a>リリース バージョンのビルド

アプリケーションのデバッグ ビルドのテストが終了したら、リリース バージョンもコンパイルしてテストする必要があります。 リリース バージョンには、アプリケーションの動作に悪影響を与える可能性があるコンパイラの最適化が組み込まれています。 たとえば、パフォーマンスを向上させるように設計されたコンパイラの最適化では、非同期アプリケーションまたはマルチスレッド アプリケーションで競合状態が生じる場合があります。

コンソール アプリケーションのリリース バージョンをビルドしてテストするには、ツール バーのビルド構成を **[デバッグ]** から **[リリース]** に変更します。

![イメージ](./media/debugging-with-visual-studio/toolbar2.png)

F5 キーを押すか、**[ビルド]** メニューの **[ソリューションのビルド]** を選ぶ、コンソール アプリケーションのリリース バージョンがコンパイルされます。 アプリケーションのデバッグ バージョンと同様に、テストできます。

アプリケーションのデバッグが終了したら、次の手順ではアプリケーションを配置可能なバージョンにして発行します。 この方法については、「[Visual Studio 2017 を使用した Hello World アプリケーションの発行](./publishing-with-visual-studio.md)」をご覧ください。
