---
title: "方法: Office プログラミングで名前付き引数と省略可能な引数を使用する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>方法: Office プログラミングで名前付き引数と省略可能な引数を使用する (C# プログラミング ガイド)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] で導入された名前付き引数と省略可能な引数を使うと、C# プログラミングの便利さ、柔軟性、読みやすさが向上します。 さらに、Microsoft Office オートメーション API などの COM インターフェイスへのアクセスが大幅に楽になります。  
  
 次の例の [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) メソッドには、列と行の数、書式設定、罫線、フォント、色など、テーブルの特性を表す 16 個のパラメーターがあります。 ほとんどの場合はこれらすべての特性に具体的な値を指定することはないので、16 個のパラメーターはすべて省略可能です。 しかし、名前付きの省略可能な引数を使わないと、各パラメーターに値またはプレースホルダー値を指定する必要があります。 名前付きの省略可能な引数を使うと、プロジェクトに必要なパラメーターの値だけを指定できます。  
  
 以下の手順を行うには、Microsoft Office Word がコンピューターにインストールされている必要があります。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>新しいコンソール アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
3.  **[Templates Categories (テンプレート カテゴリ)]** ウィンドウで、**[Visual C#]** を展開し、**[Windows]** をクリックします。  
  
4.  **[テンプレート]** ウィンドウの上部で、**[ターゲット フレームワーク]** ボックスに **[.NET Framework 4]** が表示されていることを確認します。  
  
5.  **[テンプレート]** ウィンドウで **[コンソール アプリケーション]** をクリックします。  
  
6.  **[名前]** フィールドに、プロジェクトの名前を入力します。  
  
7.  **[OK]** をクリックします。  
  
     **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。  
  
### <a name="to-add-a-reference"></a>参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトの名前を右クリックし、**[参照の追加]** をクリックします。 **[参照の追加]** ダイアログ ボックスが表示されます。  
  
2.  **[.NET]** ページの **[コンポーネント名]** の一覧で、**Microsoft.Office.Interop.Word** を選びます。  
  
3.  **[OK]** をクリックします。  
  
### <a name="to-add-necessary-using-directives"></a>ディレクティブを使用して必要なものを追加するには  
  
1.  **ソリューション エクスプローラー**で、**Program.cs** ファイルを右クリックし、**[コードの表示]** をクリックします。  
  
2.  次の `using` ディレクティブをコード ファイルの先頭に追加します。  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>Word 文書にテキストを表示するには  
  
1.  Program.cs の `Program` クラスに、Word アプリケーションと Word 文書を作成する次のメソッドを追加します。 [Add](http://go.microsoft.com/fwlink/?LinkId=145381) メソッドには、4 つの省略可能なパラメーターがあります。 この例では、それらの既定値を使います。 そのため、呼び出しステートメントに引数は必要ありません。  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  文書内でテキストを表示する場所と表示するテキストを定義する次のコードを、メソッドの最後に追加します。  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
1.  次のステートメントを Main に追加します。  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Ctrl キーを押しながら F5 キーを押してプロジェクトを実行します。 指定したテキストを含む Word 文書が表示されます。  
  
### <a name="to-change-the-text-to-a-table"></a>テキストをテーブルに変更するには  
  
1.  `ConvertToTable` メソッドを使って、テーブル内のテキストを囲みます。 このメソッドには、16 個の省略可能なパラメーターがあります。 次の例に示すように、IntelliSense では省略可能なパラメーターは角かっこで囲まれています。  
  
     ![ConvertToTable メソッドのパラメーターのリスト。](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
ConvertToTable のパラメーター  
  
     名前付きの省略可能な引数を使うと、変更するパラメーターの値だけを指定できます。 簡単なテーブルを作成するには、`DisplayInWord` メソッドの最後に次のコードを追加します。 この引数は、`range` 内のテキスト文字列のコンマがテーブルのセルを区切ることを指定します。  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     以前のバージョンの C# で `ConvertToTable` を呼び出すには、次のコードで示すように、パラメーターごとに参照引数が必要です。  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Ctrl キーを押しながら F5 キーを押してプロジェクトを実行します。  
  
### <a name="to-experiment-with-other-parameters"></a>他のパラメーターを調べるには  
  
1.  テーブルを 1 列 3 行に変更するには、`DisplayInWord` の最後の行を次のステートメントに置き換えてから、Ctrl + F5 キーを押します。  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  テーブルに対して定義済みの書式を指定するには、`DisplayInWord` の最後の行を次のステートメントに置き換えてから、Ctrl + F5 キーを押します。 書式には、[WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) 定数のどれでも指定できます。  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>例  
 ここまでの例をすべて含んだコードを次に示します。  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>関連項目  
 [名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
