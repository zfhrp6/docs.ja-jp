---
title: "partial (型) (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "partialtype"
  - "partialtype_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "部分型 [C#]"
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# partial (型) (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

部分型定義では、クラス、構造体、またはインターフェイスの定義を複数のファイルに分割することができます。  
  
 次に File1.cs の部分型定義を示します。  
  
 [!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 次に File2.cs での宣言を示します。  
  
 [!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## 解説  
 クラス型、構造体型、またはインターフェイス型を複数のファイルに分割する操作は、大規模なプロジェクトや、[Windows Forms Designer](http://msdn.microsoft.com/ja-jp/3c3d61f8-f36c-4d41-b9c3-398376fabb15) で自動生成されるコードを処理する場合に役立ちます。  部分型には、[部分メソッド](../../../csharp/language-reference/keywords/partial-method.md) が含まれる場合があります。  詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)