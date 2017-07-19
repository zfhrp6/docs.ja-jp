---
title: "方法 : 例外を明示的にスローする | Microsoft Docs"
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
  - "例外, スロー"
  - "例外, try/catch ブロック"
  - "FileNotFoundException クラス"
  - "暗黙のスロー (例外の)"
  - "try/catch ブロック"
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 例外を明示的にスローする
例外を明示的にスローするには、`throw` ステートメントを使用します。  キャッチした例外を再びスローするときにも、`throw` ステートメントを使用します。  実際のコードでは、デバッグ時に詳細情報を提供するために、再スローする例外に情報を追加すると便利です。  
  
 try ブロックと catch ブロックを使用して、発生する可能性のある <xref:System.IO.FileNotFoundException> をキャッチするコード例を次に示します。  try ブロックの後に続く catch ブロックは、データ ファイルが見つからない場合に <xref:System.IO.FileNotFoundException> をキャッチして、メッセージをコンソールに出力します。  その後の throw ステートメントでは、新しい <xref:System.IO.FileNotFoundException> をスローし、この例外にテキスト情報を追加します。  
  
## 使用例  
 [!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
 [!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  
  
## 参照  
 [方法 : Try ブロックと Catch ブロックを使用して例外をキャッチする](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [方法 : catch ブロックで特定の例外を使用する](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [方法 : finally ブロックを使用する](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)