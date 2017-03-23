---
title: "方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "デリゲート [C#], 結合"
  - "マルチキャスト デリゲート [C#]"
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 方法 : デリゲートを結合する (マルチキャスト デリゲート) (C# プログラミング ガイド)
次の例は、マルチキャスト デリゲートの作成方法を示しています。  [デリゲート](../../../csharp/language-reference/keywords/delegate.md) オブジェクトには、`+` 演算子を使用して 1 つのデリゲート インスタンスに複数のオブジェクトを割り当てることができるという特長があります。  マルチキャスト デリゲートには、割り当てられたデリゲートのリストが格納されています。  マルチキャスト デリゲートを呼び出すと、リスト内のデリゲートが順番に呼び出されます。  結合できるのは同じ型のデリゲートだけです。  
  
 `-` 演算子を使用すると、マルチキャスト デリゲートからコンポーネントのデリゲートを削除できます。  
  
## 使用例  
 [!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## 参照  
 <xref:System.MulticastDelegate>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)