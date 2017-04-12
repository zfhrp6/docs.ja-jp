---
title: "Visual Basic の新機能 | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- VB.StartPage.WhatsNew
dev_langs:
- VB
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 55cf69a06a047c12f027007ed7180bf74307f2c9
ms.lasthandoff: 03/13/2017

---
# <a name="whats-new-for-visual-basic"></a>Visual Basic の新機能
このページでは、Visual Basic の各バージョンの主要機能の名前と、言語の最新バージョンでの新機能および拡張機能の説明を一覧表示します。  
  
## <a name="previous-versions"></a>以前のバージョン  
 Visual Basic / Visual Studio .NET 2002  
 最初のリリース  
  
 Visual Basic / Visual Studio .NET 2003  
 ビット シフト演算子、ループ変数宣言  
  
 Visual Basic / Visual Studio .NET 2005  
 `My` 型とヘルパーの種類 (アプリ、コンピューター、ファイル システム、ネットワークへのアクセス  
  
 Visual Basic / Visual Studio .NET 2008  
 統合言語クエリ (LINQ)、XML リテラル、ローカル型の推定、オブジェクト初期化子、匿名型、拡張メソッド、ローカル `var` 型推論、ラムダ式、 `if` 演算子、部分メソッド、null 許容値型  
  
 Visual Basic, Visual Studio .NET 2010  
 自動実装プロパティ、コレクション初期化子、暗黙的な行の連結、動的、ジェネリック co/負の分散、グローバル名前空間のアクセス  
  
 Visual Basic / Visual Studio .NET 2012  
 `Async` / `await`、反復子、呼び出し元情報属性  
  
 Visual Basic / Visual Studio .NET 2013  
 .NET コンパイラ プラットフォーム ("Roslyn") のテクノロジのプレビュー  
  
 Visual Basic / Visual Studio .NET 2015  
 現在のバージョン (以下を参照)  
  
## <a name="current-version"></a>現在のバージョン  
 [nameof](../../csharp/language-reference/keywords/nameof.md)  
 文字列をハードコーディングせずにエラー メッセージで使用するための型またはメンバーの非修飾文字列名を取得できます。  これにより、リファクタリングするときにコードは正しい状態を保てます。  この機能は、またモデル-ビュー-コントローラーの MVC のリンクをフックし、プロパティ変更イベントを発生させるためにも役立ちます。  
  
 [文字列補間](../../csharp/language-reference/keywords/interpolated-strings.md)  
 文字列補間式を使用して、文字列を構築することができます。  補間文字列式は、式が含まれているテンプレート文字列のように見えます。  引数に関しては、補間文字列は[複合書式指定](../../standard/base-types/composite-format.md)より理解しやすくなっています。  
  
 [Null 条件付きのメンバー アクセスとインデックス作成](../../csharp/language-reference/operators/null-conditional-operators.md)  
 メンバー アクセス (`?.`) またはインデックス (`?[]`) 操作を実行する前に、構文的に非常に簡単な方法で null をテストできます。  これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます (特に、データ構造を下っていく場合)。  左のオペランドまたはオブジェクト参照が null の場合、操作は null を返します。  
  
 [複数行の文字列リテラル](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 文字列リテラルには、改行文字のシーケンスを含めることができます。  `<xml><![CDATA[...text with newlines...]]></xml>.Value` の使用に関する以前の次善策は不要になりました  
  
 コメント  
 暗黙的な行の連結の後の初期化子式内部、および LINQ 式項の間にコメントを入力できます。  
  
 スマートな完全修飾名前解決  
 `Threading.Thread.Sleep(1000)` などの特定のコードでは、以前 Visual Basic は名前空間 "Threading" を検索し、それが System.Threading と System.Windows.Threading の間であいまいであると判断し、エラーを報告していました。  これらはどちらも Visual Basic で可能な名前空間であると見なすようになりました。  コンプリート リストを表示する場合、Visual Studio エディターは、コンプリート リストの両方の種類のメンバーを一覧表示します。  
  
 年が最初にくる日付リテラル  
 日付リテラルの形式として yyyy-mm-dd `#2015-03-17 16:10 PM#` を使用できます。  
  
 ReadOnly インターフェイスのプロパティ  
 readwrite プロパティを使用して readonly インターフェイスのプロパティを実装できます。  このインターフェイスでは、最小限の機能が保証されています。これによって、実装するクラスでプロパティーが設定できなくなるということはありません。  
  
 [TypeOf \<expr> IsNot \<type>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 コードを見やすくするために、`TypeOf` を `IsNot` とともに使用できるようになりました。  
  
 [#Disable Warning \<ID> と #Enable Warning \<ID>](../../visual-basic/language-reference/directives/directives.md)  
 ソース ファイル内の領域の特定の警告を無効化および有効化することができます。  
  
 XML ドキュメント コメントの機能強化  
 ドキュメント コメントを記述する際、スマート エディターを取得し、パラメーター名の検証、`crefs` の適切な処理 (ジェネリック、演算子など)、色分け、リファクタリングのためのサポートを構築します。  
  
 [部分モジュールとインターフェイスの定義](../../visual-basic/language-reference/modifiers/partial.md)  
 クラスと構造体に加えて、部分モジュールとインターフェイスを宣言できます。  
  
 [メソッド本体内の #Region ディレクティブ](../../visual-basic/language-reference/directives/region-directive.md)  
 #Region…#End Region 区切り記号をファイルの任意の場所に挿入できます。関数内に装入することも、複数の関数本体に渡って挿入することもできます。  
  
 [上書きの定義は暗黙的オーバーロードです](../../visual-basic/language-reference/modifiers/overrides.md)  
 `Overrides` 修飾子を定義に追加する場合には、コンパイラが `Overloads`  を暗黙的に追加し、共通のケースで入力するコードを少なくできるようにします。  
  
 属性の引数で使用できる CObj  
 以前、コンパイラーは、CObj(…) を属性の構築で使用するときにそれが定数でないというエラーを報告していました。  
  
 異なるインターフェイスからのあいまいなメソッドの宣言と使用  
 以前、以下のコードはエラーになり、`IMock` を宣言したり `GetDetails` を呼び出すことができなくなっていました (これらが C# で宣言されていた場合)。  
  
```vb  
Interface ICustomer  
  Sub GetDetails(x As Integer)  
End Interface  
  
Interface ITime  
  Sub GetDetails(x As String)  
End Interface  
  
Interface IMock : Inherits ICustomer, ITime  
  Overloads Sub GetDetails(x As Char)  
End Interface  
  
Interface IMock2 : Inherits ICustomer, ITime  
End Interface  
  
```  
  
 コンパイラーは通常のオーバーロード解決規則を使用して、呼び出しに最も適切な `GetDetails` を選択するようになりました。サンプルで示されているようなインターフェイスのリレーションシップを Visual Basic で宣言できるようになりました。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 2017 の新機能](https://docs.microsoft.com/en-us/visualstudio/ide/whats-new-in-visual-studio)
