---
title: "方法: try/catch を使用して例外を処理する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外処理 [C#], try/catch ブロック"
  - "例外 [C#], try/catch ブロック"
  - "try/catch ブロック [C#]"
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 方法: try/catch を使用して例外を処理する (C# プログラミング ガイド)
[try\-catch](../../../csharp/language-reference/keywords/try-catch.md) ブロックの目的は、作業コードによって生成された例外をキャッチし、処理することです。  例外によっては、`catch` ブロックで処理し、例外を再スローせずに問題を解決できるものもありますが、多くの場合、適切な例外がスローされるようにする必要があります。  
  
## 使用例  
 この例の <xref:System.IndexOutOfRangeException> は最も適切な例外ではありません。呼び出し元から `index` 引数が渡されてエラーが発生したため、より適切なメソッドは <xref:System.ArgumentOutOfRangeException> になります。  
  
 [!code-cs[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/csharp/how-to-handle-an-excepti_1.cs)]  
  
## コメント  
 例外を発生させるコードが `try` ブロックに囲まれています。  そのすぐ後に追加されている `catch` ステートメントが、`IndexOutOfRangeException` が発生した場合に処理します。  `catch` ブロックは、`IndexOutOfRangeException` を処理し、代わりにより適切な `ArgumentOutOfRangeException` 例外をスローします。  呼び出し元にできるだけ多くの情報を提供するため、元の例外を新しい例外の <xref:System.Exception.InnerException%2A> として指定することをお勧めします。  <xref:System.Exception.InnerException%2A> プロパティは [readonly](../../../csharp/language-reference/keywords/readonly.md) なので、コンストラクターまたは新しい例外で割り当てる必要があります。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)