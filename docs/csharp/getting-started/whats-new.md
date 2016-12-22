---
title: "What&#39;s New for Visual C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9f18dc26-27fa-4603-a639-b573f07a117b
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# What&#39;s New for Visual C# #
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

このページでは、C\# の各バージョンの主要機能の名前と、言語の最新バージョンの新機能と拡張機能の説明を一覧で示します。  
  
## 以前のバージョン  
 C\# 1、Visual Studio .NET 2002  
 最初のリリース  
  
 C\# 1.1、Visual Studio .NET 2003  
 `#line` プラグマと xml ドキュメント コメント  
  
 C\# 2、Visual Studio .NET 2005  
 匿名メソッド、ジェネリック、null 許容型、反復子\/yield、`static` クラス、デリゲートの共変性\/反変性  
  
 C\# 3、Visual Studio .NET 2008  
 オブジェクト初期化子とコレクション初期化子、ラムダ式、拡張メソッド、匿名型、自動プロパティ、言語統合クエリ \(LINQ\)、匿名型、ローカル `var` 型推論、LINQ  
  
 C\# 4、Visual Studio .NET 2010  
 `Dynamic`、名前付き引数、省略可能なパラメーター、ジェネリックの共変性\/反変性  
  
 C\# 5、Visual Studio .NET 2012  
 `Async` \/ `await`、呼び出し元情報属性  
  
 Visual Studio .NET 2013  
 バグの修正、パフォーマンスの向上、および .NET コンパイラ プラットフォーム \("Roslyn"\) の Technology Preview  
  
 C\# 6、Visual Studio .NET 2015  
 現在のバージョン \(以下を参照\)  
  
## 現在のバージョン  
 [nameof](../../csharp/language-reference/keywords/nameof.md)  
 型またはメンバーの非修飾文字列名を取得し、文字列をハードコーディングせずにエラー メッセージで使用することができます。  これにより、リファクタリングするときにコードは正しい状態を保てます。  この機能は、またモデル\-ビュー\-コントローラーの MVC のリンクをフックし、プロパティ変更イベントを発生させるためにも役立ちます。  
  
 [文字列補間](../../csharp/language-reference/keywords/interpolated-strings.md)  
 文字列補間式を使用して、文字列を構築することができます。  補間文字列式は、式が含まれているテンプレート文字列のように見えます。  C\# は、式を式の結果の ToString 表現に置き換えることで文字列を作成します。  引数に関して、補間文字列は[複合書式指定](../Topic/Composite%20Formatting.md)より理解が容易です。  
  
 [Null 条件メンバー アクセスとインデックス作成](../../csharp/language-reference/operators/null-conditional-operators.md)  
 メンバー アクセス \(`?.`\) またはインデックス \(`?[]`\) 操作を実行する前に、構文的に非常に簡単な方法で null をテストできます。  これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます \(特に、データ構造を下っていく場合\)。  左のオペランドまたはオブジェクト参照が null の場合、操作は null を返します。  
  
 [インデックス初期化子](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 インデックス作成をサポートするコレクションの特定の要素を初期化できるようになりました。ディクショナリの初期化などです。  
  
 [コレクション初期化子と Add 拡張メソッド](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 コレクションに Add 拡張メソッドがある場合にコレクションの初期化子を使用できるようになりました。  以前、Add メソッドは、インスタンス メソッドである必要がありました。  
  
 **オーバーロードの解決**  
 コンパイラは、オーバーロードの解決が改善されました。結果として、期待するとおりに動作するコードが増えます。  問題に気付かなくなる可能性のある場所の 1 つは、null 許容値型を取るオーバーロードどうしの間で選択するとき、またはデリゲートを取るオーバーライドに \(ラムダの代わりに\) メソッドのグループを渡すときです。  
  
 [例外フィルター](../../csharp/language-reference/keywords/try-catch.md)  
 `catch` 句で例外フィルターを使用して、catch 句が例外を処理するかどうかを決定できます。  この機能がなければ、例外を再度スローする必要があります。この場合、再度スローされた例外で報告される呼び出し履歴がクリップされます。  
  
 [Catch ブロックと Finally ブロックでの Await](../../csharp/language-reference/keywords/try-catch.md)  
 `await` を `catch` 句と `finally` 句で使用できます。  
  
 [自動プロパティ初期化子](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 フィールドを初期化するのと同じように自動プロパティを使用できるようになりました。  
  
 [get アクセス操作子のみの自動プロパティ](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 プロパティの完全な構文を使ってプロパティを定義せずに、読み取り専用の自動プロパティを定義できるようになりました。  プロパティを宣言する場所、または型のコンストラクターでプロパティを初期化できます。  
  
 **式本体を持つ関数メンバー**  
 コードの式本体を持つメンバーを、ラムダ式で使用するのと同じ軽量構文内で宣言することができます。  「[メソッド](../../fsharp/language-reference/members/methods.md)」、「[プロパティ](../../csharp/programming-guide/classes-and-structs/properties.md)」、「[インデクサー](../../csharp/programming-guide/indexers/index.md)」、「[オーバーロードされた演算子](../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)」を参照してください。  
  
 [Using Static](../../csharp/language-reference/keywords/using-directive.md)  
 静的な型のアクセス可能な静的メンバーをインポートし、型の名前でアクセスを修飾せずにメンバーを参照することができます。  
  
## 参照  
 [Visual Studio 2015 の新機能](/visual-studio/ide/what-s-new-in-visual-studio-2015)