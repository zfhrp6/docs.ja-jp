---
title: "this (C# リファレンス) | Microsoft Docs"
description: this keyword (C# Reference)
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "this"
  - "this_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "this キーワード [C#]"
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# this (C# リファレンス)
`this` キーワードは、クラスの現在のインスタンスを参照します。拡張メソッドの最初のパラメーターの修飾子としても使用されます。  
  
> [!NOTE]
>  ここでは、クラス インスタンスでの `this` の使用について説明します。  拡張メソッドで使用する場合の詳細については、「[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。  
  
 `this` の一般的な使い方を次に示します。  
  
-   似た名前によって隠ぺいされるメンバーを修飾します。たとえば、次のように使います。  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   オブジェクトを他のメソッドにパラメーターとして渡します。たとえば、次のように使います。  
  
    ```  
    CalcTax(this);  
    ```  
  
-   インデクサーを宣言します。たとえば、次のように使います。  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 静的メンバー関数は、クラス レベルで存在し、オブジェクトの一部ではないため、`this` ポインターを持っていません。  静的メソッドで `this` を参照するとエラーになります。  
  
## 使用例  
 この例では、似た名前によって隠ぺいされている `Employee` クラスのメンバー `name` と `alias` を修飾するために `this` が使用されています。  また、別のクラスに属するメソッド `CalcTax` にオブジェクトを渡すためにも使用されています。  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)