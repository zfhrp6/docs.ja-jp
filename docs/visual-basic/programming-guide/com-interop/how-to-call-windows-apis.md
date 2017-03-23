---
title: "How to: Call Windows APIs (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "API calls"
  - "Windows API, calling"
  - "API calls, platform invoke"
  - "calls, stored procedures"
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Call Windows APIs (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

次に示すのは、user32.dll の `MessageBox` 関数を定義および呼び出して、その関数に文字列を渡す例です。  
  
## 使用例  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System> 名前空間への参照  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   メソッドが静的でないか、抽象であるか、定義済みである場合。  親の型がインターフェイスであるか、*name* または *dllName* の長さがゼロである場合  \(<xref:System.ArgumentException>\)  
  
-   *name* または *dllName* が `Nothing` である場合  \(<xref:System.ArgumentNullException>\)  
  
-   コンテナーの型が `CreateType` を使用して作成済みの型である場合  \(<xref:System.InvalidOperationException>\)  
  
## 参照  
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/ja-jp/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [プラットフォーム呼び出しの例](../Topic/Platform%20Invoke%20Examples.md)   
 [アンマネージ DLL 関数の処理](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)   
 [Defining a Method with Reflection Emit](http://msdn.microsoft.com/ja-jp/84fd3bf6-628f-41aa-83d9-b990cf926e81)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)