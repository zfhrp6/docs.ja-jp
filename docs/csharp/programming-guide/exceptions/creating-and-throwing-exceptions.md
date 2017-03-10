---
title: "例外の作成とスロー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "キャッチ (例外を) [C#]"
  - "例外 [C#], 作成"
  - "例外 [C#], スロー"
  - "スロー (例外を) [C#]"
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# 例外の作成とスロー (C# プログラミング ガイド)
例外は、プログラムの実行中にエラーが発生したことを示すために使用されます。  エラーを説明する例外オブジェクトは、作成後、[throw](../../../csharp/language-reference/keywords/throw.md) キーワードにより*スロー*されます。  ランタイムは、対応する最も近い例外ハンドラーを検索します。  
  
 次の条件の 1 つ以上が該当する場合、プログラマは例外をスローする必要があります。  
  
-   メソッドが、定義されている機能を完了できない場合。  
  
     たとえば、メソッドのパラメーターの値が無効な場合は、次のような例外をスローします。  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_1.cs)]  
  
-   オブジェクトの状態に照らして不適切な呼び出しがオブジェクトに対して行われた場合。  
  
     1 例として、読み取り専用ファイルに書き込もうとした場合が挙げられます。  オブジェクトの状態により操作が許可されない場合、<xref:System.InvalidOperationException> のインスタンスまたはこのクラスの派生に基づくオブジェクトがスローされます。  <xref:System.InvalidOperationException> オブジェクトをスローするメソッドの例を次に示します。  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_2.cs)]  
  
-   メソッドの引数が原因で例外が発生した場合。  
  
     この場合、元の例外をキャッチして、<xref:System.ArgumentException> インスタンスを作成する必要があります。  元の例外は、<xref:System.Exception.InnerException%2A> パラメーターとして <xref:System.ArgumentException> のコンストラクターに渡す必要があります。  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_3.cs)]  
  
 例外には、<xref:System.Exception.StackTrace%2A> というプロパティがあります。  この文字列には、現在の呼び出し履歴にあるメソッドの名前と、各メソッドについて例外がスローされたファイル名と行番号が含まれます。  <xref:System.Exception.StackTrace%2A> オブジェクトは、`throw` ステートメントの位置で共通言語ランタイム \(CLR: Common Language Runtime\) によって自動的に作成されるため、例外は、スタック トレースが開始される位置からスローする必要があります。  
  
 例外にはいずれも <xref:System.Exception.Message%2A> というプロパティがあります。  この文字列は、例外の原因を説明するように設定する必要があります  セキュリティ上重要な情報をメッセージ テキストに含めないように注意してください。  <xref:System.Exception.Message%2A> に加え、<xref:System.ArgumentException> には <xref:System.ArgumentException.ParamName%2A> というプロパティがあります。このプロパティは、例外がスローされる原因になった引数の名前に設定する必要があります。  プロパティ Set アクセス操作子の場合は、<xref:System.ArgumentException.ParamName%2A> を `value` に設定する必要があります。  
  
 パブリック メソッドとプロテクト メソッドのメンバーは、意図された機能を完了できない場合に例外をスローする必要があります。  スローされる例外クラスは、エラー状態に最も明確に適合する例外である必要があります。  これらの例外は、クラス機能の一部として記述する必要があり、派生クラスや元のクラスの更新では、下位互換性を確保するために同じ動作を保持する必要があります。  
  
## 例外をスローする場合に避けなければならないこと  
 例外をスローする場合に避けなければならないことを以下に示します。  
  
-   例外を通常の実行の一部として使用してプログラムのフローを変えることをしないようにしてください。  例外は、エラー状態の報告と処理のためだけに使用してください。  
  
-   そして、戻り値またはパラメーターとして返されるのではなく、スローされるようにしてください。  
  
-   独自のソース コードから <xref:System.Exception?displayProperty=fullName>、<xref:System.SystemException?displayProperty=fullName>、<xref:System.NullReferenceException?displayProperty=fullName>、または <xref:System.IndexOutOfRangeException?displayProperty=fullName> を意図的にスローしないでください。  
  
-   デバッグ モードでスローできるがリリース モードでスローできない例外を作成しないでください。  開発フェーズで実行時エラーを識別するには、代わりに Debug Assert を使用します。  
  
## 例外クラスの定義  
 プログラムでは、<xref:System> 名前空間で定義済みの、上記以外の例外クラスをスローできます。また、<xref:System.Exception> から派生させて固有の例外クラスを作成することもできます。  派生クラスでは、少なくとも 4 つのコンストラクターを定義する必要があります。1 つ目は既定のコンストラクター、2 つ目はメッセージ プロパティを設定するコンストラクター、3 つ目は <xref:System.Exception.Message%2A> と <xref:System.Exception.InnerException%2A> の両方のプロパティを設定するコンストラクターです。  そして 4 つ目のコンストラクターは、例外をシリアル化するのに使用します。  新しい例外クラスは、シリアル化できるクラスにする必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/csharp/creating-and-throwing-ex_4.cs)]  
  
 新しいプロパティを例外クラスに追加するのは、それらが提供するデータが例外を解決する上で有効な場合に限定する必要があります。  新しいプロパティを派生例外クラスに追加した場合は、`ToString()` をオーバーライドして追加情報を返す必要があります。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外階層](../Topic/Exception%20Hierarchy.md)   
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)