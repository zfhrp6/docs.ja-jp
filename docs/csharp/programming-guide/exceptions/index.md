---
title: "例外と例外処理 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 561113241f7433d8e0f7f1f1f96f0338ebe81ae3
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>例外と例外処理 (C# プログラミング ガイド)
C# 言語の例外処理機能は、プログラムの実行時に発生する予期しない状況や例外的な状況を扱うのに役立ちます。 例外処理では、キーワード `try`、`catch`、および `finally` を使用して、成功しない可能性があるアクションを試行し、適切な場合はエラーを処理して、後からリソースをクリーンアップします。 例外の発生元は、共通言語ランタイム (CLR)、.NET Framework、または任意のサード パーティ ライブラリ、またはアプリケーション コードなどさまざまです。 例外は、`throw` キーワードを使用して作成されます。  
  
 コードが直接呼び出したメソッドではなく、呼び出し履歴の下の方にある別のメソッドによって例外がスローされることも多くあります。 その場合、CLR は履歴をアンワインドし、`catch` ブロックを持つメソッドを探して特定の例外の種類がないかを調べ、もしあれば最初に見つかった `catch` ブロックを実行します。 適切な `catch` ブロックが呼び出し履歴にない場合は、プロセスが終了し、ユーザーにメッセージが表示されます。  
  
 この例では、メソッドが 0 による除算をテストしてエラーをキャッチします。 例外処理せずにプログラムは終了し、"**DivideByZeroException はハンドルされませんでした。**" というエラーが表示されます。  
  
 [!code-cs[csProgGuideExceptions 18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>例外の概要  
 例外には、次の特徴があります。  
  
-   例外はすべて最終的に `System.Exception` から派生した種類になります。  
  
-   例外をスローする可能性のあるステートメントの周囲で `try` ブロックを使用します。  
  
-   `try` ブロックで例外が発生すると、コントロールのフローが、呼び出し履歴内の関連付けられている最初の例外ハンドラーにジャンプします。 C# では、`catch` キーワードは例外ハンドラーの定義に使用されます。  
  
-   特定の例外の例外ハンドラーが存在しない場合、プログラムは実行を停止し、エラー メッセージを表示します。  
  
-   処理できない例外はキャッチしないようにして、アプリケーションを既知の状態に保ちます。 `System.Exception` をキャッチした場合は、`catch` ブロックの最後で `throw` キーワードを使用して、それを再スローします。  
  
-   `catch` ブロックで例外変数を定義した場合、それを使用して、発生した例外の種類に関する詳細を入手することができます。  
  
-   例外は、`throw` キーワードを使用してプログラムで明示的に生成することができます。  
  
-   例外オブジェクトには、呼び出し履歴の状態やエラーの説明など、エラーに関する詳細情報が含まれています。  
  
-   `finally` ブロック内のコードは、例外がスローされた場合でも実行されます。 `finally` ブロックを使用してリソースを解放します。たとえば、`try` ブロックで開かれたストリームまたはファイルを閉じます。  
  
-   .NET Framework のマネージ例外は、Win32 構造化例外処理メカニズムの上に実装されます。 詳細については、「[構造化例外処理 (C/C++)](https://docs.microsoft.com/cpp/cpp/structured-exception-handling-c-cpp)」と「[A Crash Course on the Depths of Win32 Structured Exception Handling (Win32 構造化例外処理に関する短期集中コース)」](http://go.microsoft.com/fwlink/?LinkId=119654)を参照してください。  
  
## <a name="related-sections"></a>関連項目  
 例外と例外処理の詳細については、次のトピックを参照してください。  
  
-   [例外の使用](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [例外の作成とスロー](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [コンパイラにより生成された例外](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [方法: try/catch を使用して例外を処理する (C# プログラミング ガイド)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [方法: finally を使用してクリーンアップ コードを実行する](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.SystemException>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [例外](../../../standard/exceptions/index.md)   
 [例外階層](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [信頼できる .NET コードを記述する](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [特定の例外のミニダンプ](http://go.microsoft.com/fwlink/?LinkId=112408)
