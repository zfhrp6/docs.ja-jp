---
title: "方法 : catch ブロックで特定の例外を使用する | Microsoft Docs"
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
  - "catch ブロック"
  - "例外, try/catch ブロック"
  - "try/catch ブロック"
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : catch ブロックで特定の例外を使用する
発生した例外はスタックに渡され、いずれかの catch ブロックで処理されます。  catch ステートメントの順序は重要です。  一般例外の catch ブロックの前に、特定の例外を対象とした catch ブロックを配置します。このように配置しないと、コンパイラからエラーが発行される可能性があります。  適切な catch ブロックを判別するために、例外の種類と、catch ブロックに指定されている例外の名前が一致するかどうかが調べられます。  特定の catch ブロックが存在しないが、一般の catch ブロックが存在する場合には、一般の catch ブロックによって例外がキャッチされます。  
  
 try ブロックと catch ブロックを使用して <xref:System.InvalidCastException> をキャッチするコード例を次に示します。  このコード例では、従業員レベル \(`Emlevel`\) のプロパティだけを持つ `Employee` クラスが作成されます。  `PromoteEmployee` メソッドは、オブジェクトを受け取り、従業員レベルをインクリメントするメソッドです。  <xref:System.DateTime> インスタンスが `PromoteEmployee` メソッドに渡されると、**InvalidCastException** が発生します。  
  
## 使用例  
 [!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
 [!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
 [!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]  
  
 catch ブロックによってキャッチされなかった例外は、共通言語ランタイムによってキャッチされます。  ランタイムの構成に応じて、デバッグ ダイアログ ボックスが表示されるか、またはプログラムにより処理が停止されて例外情報のダイアログ ボックスが表示されます。  デバッグの詳細については、「[アプリケーションのデバッグとプロファイリング](../../../docs/framework/debug-trace-profile/index.md)」を参照してください。  
  
## 参照  
 [方法 : Try ブロックと Catch ブロックを使用して例外をキャッチする](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [方法 : 例外を明示的にスローする](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)   
 [方法 : ユーザー定義の例外を作成する](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)   
 [方法 : finally ブロックを使用する](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)   
 [Exception クラスとプロパティ](../../../docs/standard/exceptions/exception-class-and-properties.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)