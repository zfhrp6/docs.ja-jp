---
title: "Visual Basic Coding Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "coding conventions, Visual Basic"
  - "examples [Visual Basic], coding conventions"
  - "Visual Basic code, conventions"
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 48
---
# Visual Basic Coding Conventions
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Microsoft は、ここで示すガイドラインに従ってサンプルおよびドキュメントを開発しています。  同じコーディング規則に従うと、次のような利点があります。  
  
-   コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。  
  
-   これまでの経験に基づいて推測できるようになるため、コードをすばやく理解できます。  
  
-   コードのコピー、変更、保守がより簡単になります。  
  
-   コードが Visual Basic の "ベスト プラクティス" に従っていることを確認できます。  
  
## 名前付け規則  
  
-   名前付けのガイドラインについては、「[名前付けのガイドライン](../Topic/Naming%20Guidelines.md)」を参照してください。  
  
-   "My" または "my" を変数名の一部として使用しないようにします。  `My` オブジェクトとの混同を招くからです。  
  
-   自動生成されたコードに含まれるオブジェクトの名前をこのガイドラインに合わせて変更する必要はありません。  
  
## レイアウト規則  
  
-   タブを空白として挿入し、4 文字インデントによるスマート インデントを使用します。  
  
-   コード エディターで **\[コードの再フォーマット\]** を使用してコードの書式を再設定します。  詳細については、「[\[オプション\]、\[テキスト エディター\]、\[基本\] \(Visual Basic\)](/visual-studio/ide/reference/options-text-editor-basic-visual-basic)」を参照してください。  
  
-   1 つの行には 1 つのステートメントのみを記述します。  Visual Basic の行区切り記号 \(:\) は使用しないでください。  
  
-   言語で許可される場所では、明示的な行継続文字 "\_" ではなく暗黙的な行継続を使用します。  
  
-   1 つの行には 1 つの宣言のみを記述します。  
  
-   **\[コードの再フォーマット\]** で継続行が自動的に書式設定されない場合は、継続行のインデントを手動で 1 タブ ストップに設定します。  ただし、リストの項目は常に左揃えにします。  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。  
  
## コメント規則  
  
-   コメントは、コード行の末尾ではなく別の行に記述します。  
  
-   英語でコメントを記述する場合、コメント テキストの始まりには英大文字を使用し、終わりにはピリオドを使用します。  
  
-   コメント デリミター \('\) とコメント テキストの間に空白を 1 つ挿入します。  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   アスタリスク \(\*\) を整形したブロックでコメントを囲まないようにします。  
  
## プログラムの構造  
  
-   `Main` メソッドを使用するときには、新しいコンソール アプリケーションの既定の構造を使用し、コマンド ライン引数には `My` を使用します。  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## 言語ガイドライン  
  
### 文字列型 \(String\)  
  
-   文字列を連結するには、アンパサンド \(&\) を使用します。  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   ループ内での文字列の追加には <xref:System.Text.StringBuilder> オブジェクトを使用します。  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### イベント ハンドラー内の厳密でないデリゲート  
 イベント ハンドラーの引数 \(Object および EventArgs\) は明示的に修飾しません。  イベントに渡されるイベント引数 \(sender as Object、e as EventArgs など\) を使用しない場合は、厳密でないデリゲートを使用して、コードでイベント引数を省略します。  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### Unsigned データ型  
  
-   特に必要でない限り、unsigned 型ではなく `Integer` を使用します。  
  
### 配列  
  
-   宣言行で配列を初期化するときは短い構文を使用します。  たとえば、次のような構文を使用します。  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     次のような構文は使用しません。  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   配列指定子は、変数ではなく型に指定します。  たとえば、次のような構文を使用します。  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     次のような構文は使用しません。  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   基本データ型の配列の宣言と初期化では、{ } 構文を使用します。  たとえば、次のような構文を使用します。  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     次のような構文は使用しません。  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### With キーワードの使用  
 同じオブジェクトの呼び出しを複数回使用する場合には、`With` キーワードの使用を検討します。  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### 例外処理を使用する場合の Try...Catch\/Using ステートメントの使用  
 `On Error Goto` は使用しないでください。  
  
### IsNot キーワードの使用  
 `Not...Is Nothing` の代わりに `IsNot` キーワードを使用します。  
  
### New キーワード  
  
-   短い形式のインスタンス化を使用します。  たとえば、次のような構文を使用します。  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     この行は次の行と同じ結果をもたらします。  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   新しいオブジェクトには、パラメーターなしのコンストラクターの代わりにオブジェクト初期化子を使用します。  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### イベント処理  
  
-   `AddHandler` ではなく `Handles` を使用します。  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   `AddressOf` を使用し、デリゲートの明示的なインスタンス化は避けます。  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   イベントを定義するときには、短い構文を使用し、デリゲートの定義はコンパイラに任せます。  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   `RaiseEvent` メソッドを呼び出す前にイベントが `Nothing` \(null\) かどうか確認しないようにします。  `RaiseEvent` は、イベントを発生させる前に `Nothing` かどうか確認します。  
  
### 共有メンバーの使用  
 `Shared` メンバーの呼び出しにはクラス名を使用し、インスタンス変数からは行わないようにします。  
  
### XML リテラルの使用  
 XML リテラルを使用すると、XML 操作時に行う最も一般的なタスク \(読み込み、クエリ、変換など\) を簡素化できます。  XML を使用して開発を行う場合は、次のガイドラインに従います。  
  
-   XML API を直接呼び出す代わりに XML リテラルを使用して XML ドキュメントおよびフラグメントを作成します。  
  
-   ファイル レベルまたはプロジェクト レベルで XML 名前空間をインポートし、XML リテラルによるパフォーマンスの最適化を利用します。  
  
-   XML 軸プロパティを使用して XML ドキュメント内の要素と属性にアクセスします。  
  
-   `Add` メソッドなどの API 呼び出しを使用する代わりに、埋め込み式を使用して既存の値から値を組み込んで XML を作成します。  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### LINQ クエリ  
  
-   クエリ変数にはわかりやすい名前を使用します。  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   クエリ内で要素の名前を指定して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。  たとえば、クエリが顧客名と注文 ID を返す場合、それらの名前を結果の `Name` と `ID` のままにはせずに変更します。  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   クエリ変数と範囲変数の宣言で型の推論を使用します。  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   各クエリ句を `From` ステートメントの下に揃えます。  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   `Where` 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   `Where` 句を使用して暗黙的に結合操作を定義する代わりに、`Join` 句を使用して明示的に結合操作を定義します。  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## 参照  
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)