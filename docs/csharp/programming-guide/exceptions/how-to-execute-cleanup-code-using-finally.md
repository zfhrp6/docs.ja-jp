---
title: "方法: finally を使用してクリーンアップ コードを実行する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外処理 [C#], try/finally ブロック"
  - "例外 [C#], try/finally ブロック"
  - "try/finally ブロック [C#]"
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 方法: finally を使用してクリーンアップ コードを実行する (C# プログラミング ガイド)
`finally` ステートメントの目的は、例外がスローされた場合でも、オブジェクト \(一般に外部リソースを保持しているオブジェクト\) に対して必要なクリーンアップを即座に実行できるようにすることです。  次のように、共通言語ランタイムによってオブジェクトがガベージ コレクションされるまで待機する代わりに、オブジェクトを使用した後すぐに <xref:System.IO.FileStream> で <xref:System.IO.Stream.Close%2A> を呼び出すというのも、このようなクリーンアップの一例です。  
  
 [!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/csharp/how-to-execute-cleanup-c_1.cs)]  
  
## 使用例  
 上のコードを `try-catch-finally` ステートメントに変えるには、次のようにクリーンアップ コードを作業コードから分離します。  
  
 [!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/csharp/how-to-execute-cleanup-c_2.cs)]  
  
 例外は `OpenWrite()` 呼び出しの前に `try` ブロック内でどの時点でも発生する可能性があるため、または `OpenWrite()` 呼び出し自体が失敗する可能性があるため、ファイルを閉じようとしたときにそのファイルが開いているという保証はありません。  `finally` ブロックでは、<xref:System.IO.Stream.Close%2A> メソッドを呼び出す前に、<xref:System.IO.FileStream> オブジェクトが `null` でないことを確認するチェックを行います。  この `null` チェックを行わないと、`finally` ブロックから <xref:System.NullReferenceException> がスローされる可能性がありますが、`finally` ブロックにおける例外のスローはできるだけ回避する必要があります。  
  
 データベース接続も、`finally` ブロックで閉じられる対象になります。  データベース サーバーに許容される接続数は限られている場合があるため、データベース接続はできるだけ早く閉じる必要があります。  接続を閉じる前に例外がスローされる場合でも、ガベージ コレクションを待機するより、`finally` ブロックを使用することをお勧めします。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)