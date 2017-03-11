---
title: "Events of shared WithEvents variables cannot be handled by non-shared methods | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30594"
  - "vbc30594"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30594"
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Events of shared WithEvents variables cannot be handled by non-shared methods
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Shared` 修飾子を使って宣言されている変数は共有変数です。  共有変数は、ただ 1 つのストレージ位置を表します。  `WithEvents` 修飾子付きで宣言された変数は、変数が属している型が変数によって生成されるイベントのセットを処理することを表しています。  変数に値を代入すると、`WithEvents` 宣言によって作成されたプロパティが既存の各イベント ハンドラーをアンフックし、`Add` メソッドを介して新しいイベント ハンドラーをフックします。  
  
 **Error ID:** BC30594  
  
### このエラーを解決するには  
  
-   イベント ハンドラーを `Shared` で宣言します。  
  
## 参照  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)