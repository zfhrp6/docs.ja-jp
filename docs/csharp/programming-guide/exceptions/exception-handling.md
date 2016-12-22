---
title: "例外処理 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外処理 [C#], 例外処理の概要"
  - "例外 [C#], 処理"
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 例外処理 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# では、例外による影響を受けることがあるコードを分割するために [try](../../../csharp/language-reference/keywords/try-catch.md) ブロックを使用します。  その結果発生する例外を処理するためには、これに関連付けられた [catch](../../../csharp/language-reference/keywords/try-catch.md) ブロックを使用します。  また、[finally](../../../csharp/language-reference/keywords/try-finally.md) ブロックには、`try` ブロックで例外がスローされたかどうかに関係なく実行されるコード \(`try` ブロックで割り当てたリリースの解放など\) が置かれます。  `try` ブロックには、関連付けられた `catch` ブロックと `finally` ブロックの少なくとも 1 つ、またはその両方が必要です。  
  
 次の例では、`try-catch` ステートメント、`try-finally` ステートメント、および `try-catch-finally` ステートメントについて示します。  
  
 [!code-cs[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-cs[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-cs[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 `catch` ブロックも `finally` ブロックも存在しない `try` ブロックは、コンパイラ エラーになります。  
  
## catch ブロック  
 `catch` ブロックでは、キャッチする例外の種類を指定できます。  種類の指定は、*例外フィルター*と呼ばれます。  例外の種類は、<xref:System.Exception> から派生する必要があります。  通常、例外フィルターとして <xref:System.Exception> は指定しません。ただし、`try` ブロックでスローされる例外の処理方法が判明している場合、または `catch` ブロックの末尾に [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを挿入している場合を除きます。  
  
 異なる例外フィルターを持つ複数の `catch` ブロックを使用できます。  例外がスローされるたびに、コード内の `catch` ブロックが上から下に評価されますが、実行される `catch` ブロックは 1 つだけです。  実行されるのは、スローされた例外の種類または基本クラスを正確に指定している最初の `catch` ブロックです。  一致する例外フィルターを指定する `catch` ブロックがない場合は、フィルターを持たない `catch` ブロックが選択されます \(そのようなブロックがステートメント内に存在する場合\)。  最も限定的な \(つまり、最派生の\) 例外の種類を持つ `catch` ブロックを最初に配置することが重要です。  
  
 次の条件に当てはまる場合は、例外をキャッチする必要があります。  
  
-   例外がスローされた原因を明確に把握しており、<xref:System.IO.FileNotFoundException> オブジェクトをキャッチしたときにユーザーに新しいファイル名の入力を求めるなど、特定の回復措置を実装できる場合。  
  
-   より限定的な新しい例外を生成し、スローできる場合。  
  
     [!code-cs[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   例外を部分的に処理してから、他の処理に例外を渡すことがあります。  次の例では、例外を再スローする前にエラー ログにエントリを追加するために `catch` ブロックが使用されています。  
  
     [!code-cs[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## finally ブロック  
 `finally` ブロックでは、`try` ブロックで実行されるアクションをクリーンアップできます。  `finally` ブロックが存在する場合、このブロックは、`try` ブロックと、一致した `catch` ブロックの後で最後に実行されます。  `finally` ブロックは、例外がスローされたかどうか、または例外の種類に一致する `catch` ブロックが見つかったかどうかとは無関係に常に実行されます。  
  
 `finally` ブロックを使用すると、ガベージ コレクターが実行時にオブジェクトを終了するのを待たずに、ファイル ストリーム、データベース接続、グラフィックス ハンドルなどのリソースを解放できます。  詳細については、「[using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
 次の例では、`finally` ブロックを使用して、`try` ブロックで開かれたファイルを閉じます。  ファイルを閉じる前に、ファイル ハンドルの状態がチェックされることに注意してください。  `try` ブロックでファイルを開くことができない場合でも、ファイル ハンドルの値は `null` のままであるため、`finally` ブロックでファイルを閉じようとすることはありません。  また、`try` ブロックで正常にファイルが開かれている場合は、`finally` ブロックでファイルが閉じられます。  
  
 [!code-cs[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)