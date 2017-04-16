---
title: "方法 : finally ブロックを使用する | Microsoft Docs"
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
  - "ArgumentOutOfRangeException クラス"
  - "例外, finally ブロック"
  - "例外, try/catch ブロック"
  - "finally ブロック"
  - "try/catch ブロック"
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : finally ブロックを使用する
例外が発生すると、処理が中止され、最も近い例外ハンドラーへ制御が渡されます。  このため、常に呼び出されるはずのコード行が実行されないことがよくあります。  例外がスローされても、ファイルのクローズなどの一部のリソース クリーンアップ処理は常に実行されます。  クリーンアップ処理を常に実行するには、finally ブロックを使用します。  例外がスローされたかどうかに関係なく、finally ブロックは常に実行されます。  
  
 try ブロックと catch ブロックを使用して <xref:System.ArgumentOutOfRangeException> をキャッチするコード例を次に示します。  `Main` メソッドは 2 つの配列を作成し、1 つの配列をもう 1 つの配列へコピーしようとします。  このコピー操作により **ArgumentOutOfRangeException** が生成されるため、コンソールへエラーが出力されます。  finally ブロックは、コピー操作の結果に関係なく実行されます。  
  
## 使用例  
 [!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
 [!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
 [!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  
  
## 参照  
 [方法 : Try ブロックと Catch ブロックを使用して例外をキャッチする](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [方法 : 例外を明示的にスローする](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)   
 [方法 : ユーザー定義の例外を作成する](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)