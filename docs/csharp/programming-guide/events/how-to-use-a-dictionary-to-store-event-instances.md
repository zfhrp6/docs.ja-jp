---
title: "方法 : ディクショナリを使用してイベント インスタンスを格納する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "イベント [C#], 格納 (インスタンスをディクショナリに)"
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : ディクショナリを使用してイベント インスタンスを格納する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

多数のイベントを公開する場合に `accessor-declarations` を使用すると、各イベントにフィールドを割り当てる代わりにディクショナリを使用してイベント インスタンスを格納できます。  これは、多数のイベントがあるものの、それらのほとんどが実装されそうもない場合にだけ便利です。  
  
## 使用例  
 [!CODE [csProgGuideEvents#9](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEvents#9)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)