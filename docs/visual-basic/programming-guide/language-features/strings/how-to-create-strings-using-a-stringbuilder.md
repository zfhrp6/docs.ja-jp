---
title: "How to: Create Strings Using a StringBuilder in Visual Basic | Microsoft Docs"
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
  - "StringBuilder class"
  - "strings [Visual Basic], using StringBuilder"
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# How to: Create Strings Using a StringBuilder in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

この例では、<xref:System.Text.StringBuilder> クラスを使って、短い文字列から長い文字列を作成します。  <xref:System.Text.StringBuilder> クラスは、多くの文字列を結合する場合、`&=` 演算子よりも効率的です。  
  
## 使用例  
 次の例では、<xref:System.Text.StringBuilder> クラスのインスタンスを作成し、1000 の文字列をそのインスタンスに結合し、最終的な文字列を返します。  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## 参照  
 [StringBuilder クラスの使用](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)   
 [&\= Operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [新しい文字列の作成](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [文字列の操作](../Topic/Manipulating%20Strings%20in%20the%20.NET%20Framework.md)   
 [Strings Sample](http://msdn.microsoft.com/ja-jp/be9e82a3-dc95-4aaa-9396-61b66e467e02)