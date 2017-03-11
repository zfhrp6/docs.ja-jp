---
title: "new 制約 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "new 制約キーワード [C#]"
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# new 制約 (C# リファレンス)
`new` 制約は、ジェネリック クラス宣言内のすべての型引数に、パブリックなパラメーターなしのコンストラクターが必要であることを示します。  new 制約を使用する場合、型を抽象型にすることはできません。  
  
## 使用例  
 `new` 制約は、次の例に示すように、ジェネリック クラスで型の新しいインスタンスを作成する場合に型パラメーターに適用されます。  
  
 [!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#5)]  
  
## 使用例  
 `new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。  
  
 [!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#6)]  
  
 詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)