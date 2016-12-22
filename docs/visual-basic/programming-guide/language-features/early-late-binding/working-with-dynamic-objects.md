---
title: "Working with Dynamic Objects (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dynamic objects [Visual Basic]"
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Working with Dynamic Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

動的オブジェクトを使用すると、`Object` 型とは別の方法で、実行時にオブジェクトに遅延バインディングできます。  動的オブジェクトは、<xref:System.Dynamic> 名前空間に定義されている動的インターフェイスを使用して、実行時にプロパティやメソッドなどのメンバーを公開します。  <xref:System.Dynamic> 名前空間のクラスを使用して、静的な型または形式が一致しないデータ構造体を操作するオブジェクトを作成できます。  また、IronPython や IronRuby などの動的言語で定義されている動的オブジェクトも使用できます。  動的オブジェクトの作成方法の例または動的言語で定義されている動的オブジェクトの使用方法の例については、「[チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)」、「<xref:System.Dynamic.DynamicObject>」、または「<xref:System.Dynamic.ExpandoObject>」を参照してください。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、<xref:System.Dynamic.IDynamicMetaObjectProvider> インターフェイスを使用することで、IronPython や IronRuby などの動的言語および動的言語ランタイムからのオブジェクトにバインドされます。  `IDynamicMetaObjectProvider` インターフェイスを実装するクラスには、<xref:System.Dynamic.DynamicObject> クラスや <xref:System.Dynamic.ExpandoObject> クラスがあります。  
  
 `IDynamicMetaObjectProvider` インターフェイスを実装するオブジェクトに対して遅延バインディングによる呼び出しが行われる場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はそのインターフェイスを使用して動的オブジェクトにバインドされます。  `IDynamicMetaObjectProvider` インターフェイスを実装しないオブジェクトに対して遅延バインディングによる呼び出しが行われる場合、または `IDynamicMetaObjectProvider` に対する呼び出しに失敗した場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ランタイムの遅延バインディングによる呼び出し機能を使用することで、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はその動的オブジェクトにバインドされます。  
  
## 参照  
 <xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject>   
 [チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)