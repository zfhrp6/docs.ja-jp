---
title: "typeof (C# リファレンス) | Microsoft Docs"
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
  - "typeof"
  - "typeof_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "typeof キーワード [C#]"
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# typeof (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

型の `System.Type` オブジェクトを取得します。  `typeof` 式は次の形式をとります。  
  
```  
System.Type type = typeof(int);  
```  
  
## 解説  
 式の実行時の型を取得するには、次の例のように、.NET Framework のメソッド <xref:System.Object.GetType%2A> を使用できます。  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` 演算子はオーバーロードできません。  
  
 `typeof` 演算子は、オープン ジェネリック型に使用することもできます。  複数の型パラメーターが指定されている型では、仕様上、適切な数のコンマが使用されている必要があります。  メソッドの戻り値の型がジェネリック <xref:System.Collections.Generic.IEnumerable%601> かどうかを確認する方法を次の例に示します。  メソッドが MethodInfo 型のインスタンスであることを想定しています。  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## 使用例  
 [!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## 使用例  
 次の例では、<xref:System.Object.GetType%2A> メソッドを使用して、数値計算の結果の格納に使用する型が決定されます。  これは、結果として導かれた数値のストレージ要件によって異なります。  
  
 [!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 <xref:System.Type?displayProperty=fullName>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)