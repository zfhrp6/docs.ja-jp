---
title: "方法: bool? から bool に安全にキャストする (C# プログラミング ガイド) | Microsoft Docs"
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
  - "キャスト [C#], null 許容型"
  - "null 許容型 [C#], キャスト (bool? から bool へ)"
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Null 許容 `bool?` 型は、`true`、`false`、`null` の 3 つの異なる値を格納できます。  そのため、`bool?` 型は、`if`、`for`、`while` などの条件文で使用できません。  たとえば、次のコードはコンパイラ エラーになります。  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 コンパイルできないのは、条件文のコンテキストで `null` の意味があいまいだからです。  条件付きステートメントで `bool?` を使用するにはまず、その <xref:System.Nullable%601.HasValue%2A> プロパティをチェックしてその値が `null` でないことを確認します。次に、`bool` にキャストします。  詳細については、「[bool](../../../csharp/language-reference/keywords/bool.md)」を参照してください。  `bool?` でキャストを実行するときに値が `null` になっていると、条件テストで <xref:System.InvalidOperationException> がスローされます。  次の例は、`bool?` から `bool` に安全にキャストするための 1 つの方法を示しています。  
  
## 使用例  
  
```c#  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [リテラル キーワード](../../../csharp/language-reference/keywords/literal-keywords.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [?? 演算子](../../../csharp/language-reference/operators/null-conditional-operator.md)