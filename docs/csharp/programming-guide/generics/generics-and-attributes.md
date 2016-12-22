---
title: "ジェネリックと属性 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "属性 [C#], ジェネリック"
  - "ジェネリック [C#], 属性"
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ジェネリックと属性 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

属性は、非ジェネリック型と同じ方法でジェネリック型に適用できます。  属性の適用の詳細については、「[属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 カスタム属性は、オープン ジェネリック型のみを参照できます。オープン ジェネリック型は、型引数が与えられていないジェネリック型です。クローズ構築ジェネリック型は、すべての型パラメーターに引数が与えられています。  
  
 次の例では、このカスタム属性を使用しています。  
  
 [!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 属性は、次のようにオープン ジェネリック型を参照できます。  
  
 [!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 適切な数のコンマを使用して複数の型パラメーターを指定します。  この例では、`GenericClass2` に 2 つの型パラメーターがあります。  
  
 [!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 属性は、クローズ構築ジェネリック型を参照できます。  
  
 [!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 ジェネリック型のパラメーターを参照する属性は、コンパイル時のエラーを発生させます。  
  
 [!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 ジェネリック型は <xref:System.Attribute> から継承できません。  
  
 [!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 ジェネリック型または型パラメーターに関する情報を実行時に取得するには、<xref:System.Reflection> というメソッドを使用できます。  詳細については、「[ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../visual-basic/reference/command-line-compiler/index.md)   
 [属性](../Topic/Extending%20Metadata%20Using%20Attributes.md)