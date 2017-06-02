---
title: "ユーザー フィルター例外ハンドラーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "例外, ユーザー フィルター"
  - "ユーザー フィルター例外"
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# ユーザー フィルター例外ハンドラーの使用
現在 Visual Basic では、ユーザー フィルター例外をサポートしています。  ユーザー フィルター例外ハンドラーは、独自に定義された例外の条件に基づいて例外をキャッチおよび処理します。  これらのハンドラーでは、**Catch** ステートメントを **When** キーワードと一緒に使用します。  
  
 特定の例外オブジェクトが複数のエラーに対応するときにこの手法を使用すると便利です。  通常、このような例外オブジェクトには、エラーに関連付けられた特定のエラー コードが格納されているプロパティがあります。  **Catch** 句で処理する特定のエラーだけを選択するには、エラー コード プロパティを使用した式を作成します。  
  
 `When` キーワードが指定された **Catch** ステートメントを次の Visual Basic コード例に示します。  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 ユーザー フィルター句の式が制限されることはありません。  ユーザー フィルター式の実行中に例外が発生すると、その例外は破棄され、そのフィルター式は false と評価されたと見なされます。  この場合、共通言語ランタイムでは、現在の例外に対応するハンドラーの検索が継続されます。  
  
## 特定の例外とユーザー フィルター句の組み合わせ  
 catch ステートメントには、特定の例外とユーザー フィルター句の両方を記述できます。  ランタイムでは、特定の例外が最初にテストされます。  特定の例外がテストを通過すると、次にユーザー フィルターが実行されます。  汎用フィルターには、クラス フィルターで宣言されている変数への参照を含めることができます。  2 つのフィルター句の順序は一定であり、変更できないことに注意してください。  
  
 `ClassLoadException` という例外が指定された **Catch** ステートメントと、**When** キーワードを使用したユーザー フィルター句の Visual Basic コード例を次に示します。  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  
  
## 参照  
 [方法 : Try ブロックと Catch ブロックを使用して例外をキャッチする](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [方法 : catch ブロックで特定の例外を使用する](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [例外の推奨事項](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)