---
title: "方法: as 演算子と is 演算子を使用して安全にキャストする (C# プログラミング ガイド) | Microsoft Docs"
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
  - "as 演算子 [C#]"
  - "キャスト演算子 [C#], as 演算子と is 演算子"
  - "is 演算子 [C#]"
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: as 演算子と is 演算子を使用して安全にキャストする (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

オブジェクトはポリモーフィックであるため、基本クラス型の変数のための派生型を保持できます。  派生型のメソッドにアクセスするには、値をキャストしてその派生型に戻す必要があります。  ただし、このような場合に単純にキャストを実行すると、<xref:System.InvalidCastException> がスローされる危険性があります。  このため、C\# には、[is](../../../csharp/language-reference/keywords/is.md) 演算子と [as](../../../csharp/language-reference/keywords/as.md) 演算子が用意されています。  これらの演算子を使用すると、例外がスローされることなくキャストが成功するかどうかをテストできます。  通常、`as` 演算子のほうが、キャストが正しく実行できる場合に、キャスト値を実際に返すのでより効率的です。  `is` 演算子は、ブール値のみ返します。  したがって、オブジェクトの型の確認のみ行い、キャストは行う必要がない場合に使用できます。  
  
## 使用例  
 `is` 演算子および `as` 演算子を使用して、例外がスローされる危険性を回避しながら、参照型を別の参照型にキャストする方法を次の例に示します。  この例では、null 許容型に対し `as` 演算子を使用する方法も示します。  
  
 [!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## 参照  
 [型](../../../visual-basic/reference/command-line-compiler/index.md)   
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)