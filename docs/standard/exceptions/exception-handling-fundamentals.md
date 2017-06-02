---
title: "例外処理の基本事項 | Microsoft Docs"
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
  - "共通言語ランタイム, 例外"
  - "例外, 例"
  - "ランタイム, 例外"
ms.assetid: e865d48c-b862-4448-833e-09fcd48adf6b
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 例外処理の基本事項
共通言語ランタイムは、例外オブジェクトとプロテクト ブロック コードの概念に基づいた例外処理モデルをサポートしています。  例外が発生すると、その例外を表すオブジェクトがランタイムによって作成されます。  独自の例外クラスを作成するには、適切な基本例外の派生クラスを使用します。  
  
 ランタイムを使用するすべての言語で、例外は類似した方法で処理されます。  各言語で、try、catch、finally の各ブロックを使用した構造化例外処理が使用されます。  このセクションでは、基本的な例外処理のいくつかの例を示して説明します。  
  
## このセクションの内容  
 [方法 : Try ブロックと Catch ブロックを使用して例外をキャッチする](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)  
 try ブロックと catch ブロックを使用して例外を処理する方法について説明します。  
  
 [方法 : catch ブロックで特定の例外を使用する](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)  
 特定の例外をキャッチする方法について説明します。  
  
 [方法 : 例外を明示的にスローする](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)  
 例外をスローする方法と、例外をキャッチして再びスローする方法について説明します。  
  
 [方法 : ユーザー定義の例外を作成する](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)  
 独自の例外クラスを作成する方法について説明します。  
  
 [ユーザー フィルター ハンドラーの使用](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)  
 フィルター例外を設定する方法について説明します。  
  
 [方法 : finally ブロックを使用する](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)  
 例外ブロックでの finally ステートメントの使用方法について説明します。  
  
## 関連項目  
 [例外](../../../docs/standard/exceptions/index.md)  
 共通言語ランタイムの例外を概説します。  
  
 [Exception クラスとプロパティ](../../../docs/standard/exceptions/exception-class-and-properties.md)  
 例外オブジェクトの要素について説明します。