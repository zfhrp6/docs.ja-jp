---
title: "方法: Office プログラミングで名前付き引数と省略可能な引数を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "名前付き引数と省略可能な引数 [C#], Office プログラミング"
  - "名前付き引数 [C#], Office プログラミング"
  - "省略可能な引数 [C#], Office プログラミング"
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 34
---
# 方法: Office プログラミングで名前付き引数と省略可能な引数を使用する (C# プログラミング ガイド)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)] に導入された名前付き引数と省略可能な引数により、C\# プログラミングの利便性、柔軟性、および読みやすさが向上しました。また、これらの機能によって、Microsoft Office オートメーション API などの COM インターフェイスへのアクセスも容易になります。  
  
 次の例では、[ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) メソッドに 16 個のパラメーターがあります。これらのパラメーターは、列と行の数、書式設定、境界線、フォント、色などの表の特性を表します。  ほとんどの場合どのパラメーターにも特定の値を指定する必要がないため、16 個のパラメーターはすべて省略可能です。  ただし、名前付き引数と省略可能な引数を使用しない場合は、各パラメーターに対して値またはプレースホルダー値を指定する必要があります。  名前付き引数および省略可能な引数を使用する場合は、プロジェクトに必要なパラメーターのみに値を指定します。  
  
 以下の手順を実行するには、Microsoft Office Word がコンピューターにインストールされている必要があります。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 新しいコンソール アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  **\[テンプレート カテゴリ\]** ペインで、**\[Visual C\#\]** を展開し、**\[Windows\]** をクリックします。  
  
4.  **\[テンプレート\]** ペインの最上部で、**\[.NET Framework 4\]** が **\[ターゲット フレームワーク\]** ボックスに表示されていることを確認します。  
  
5.  **\[テンプレート\]** ペインの **\[コンソール アプリケーション\]** をクリックします。  
  
6.  **\[名前\]** フィールドにプロジェクトの名前を入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。  
  
### 参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクト名を右クリックし、**\[参照の追加\]** をクリックします。  **\[参照の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[.NET\]** ページの **\[コンポーネント名\]** のボックスの一覧で、**\[Microsoft.Office.Interop.Word\]** を選択します。  
  
3.  **\[OK\]** をクリックします。  
  
### 必要な using ディレクティブを追加するには  
  
1.  **ソリューション エクスプローラー**で、**Program.cs** ファイルを右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  コード ファイルの先頭に、次の `using` ディレクティブを追加します。  
  
     [!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#4)]  
  
### Word 文書にテキストを表示するには  
  
1.  Program.cs の `Program` クラスでは、Word アプリケーションおよび Word 文書を作成する次のメソッドを追加します。  [Add](http://go.microsoft.com/fwlink/?LinkId=145381) メソッドには、4 つの省略可能なパラメーターがあります。  この例では、それらのパラメーターの既定値を使用します。  そのため、呼び出しステートメントには引数を指定する必要がありません。  
  
     [!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#6)]  
  
2.  文書のテキストを表示する場所と表示するテキストの内容を定義するメソッドの末尾に次のコードを追加します。  
  
     [!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#7)]  
  
### アプリケーションを実行するには  
  
1.  Main を呼び出すための次のステートメントを追加します。  
  
     [!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#8)]  
  
2.  Ctrl キーを押しながら F5 キーを押してプロジェクトを実行します。  指定したテキストを含む Word 文書が表示されます。  
  
### 表のテキストを変更するには  
  
1.  `ConvertToTable` メソッドを使用して、表のテキストを囲みます。  このメソッドには、16 個の省略可能なパラメーターがあります。  次の例に示すように、IntelliSense では、省略可能なパラメーターを角かっこで囲みます。  
  
     ![ConvertToTable メソッドのパラメーターのリスト](../../../csharp/programming-guide/classes-and-structs/media/convert-tableparameters.png "Convert\_TableParameters")  
ConvertToTable のパラメーター  
  
     名前付き引数と省略可能な引数を使用すると、変更するパラメーターのみの値を指定できます。  `DisplayInWord` メソッドの末尾に次のコードを追加して、単純な表を作成します。  この引数では、`range` のテキスト文字列内のコンマで、テーブルのセルを区切るように指定します。  
  
     [!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#9)]  
  
     旧バージョンの C\# では、次のコードに示すように、`ConvertToTable` の呼び出しに各パラメーターの参照引数が必要です。  
  
     [!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#14)]  
  
2.  Ctrl キーを押しながら F5 キーを押してプロジェクトを実行します。  
  
### 他のパラメーターを試してみるには  
  
1.  1 つの列と 3 つの行を含むように表を変更するには、`DisplayInWord` の最後の行を次のステートメントに置き換え、Ctrl キーを押しながら F5 キーを押します。  
  
     [!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#10)]  
  
2.  表の定義済みの形式を指定するには、`DisplayInWord` の最後の行を次のステートメントに置き換え、Ctrl キーを押しながら F5 キーを押します。   形式は [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) のいずれかの定数とすることができます。  
  
     [!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#11)]  
  
## 使用例  
 この例のコード全体を次に示します。  
  
 [!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#12)]  
  
## 参照  
 [名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)