---
title: "readonly (C# リファレンス) | Microsoft Docs"
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
  - "readonly_CSharpKeyword"
  - "readonly"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "readonly キーワード [C#]"
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# readonly (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`readonly` キーワードは、フィールドに使用できる修飾子です。  フィールド宣言が `readonly` 修飾子を含む場合、宣言によって導入されるフィールドへの代入は、宣言の一部としてだけ、または同じクラスのコンストラクター内でだけ発生できます。  
  
## 使用例  
 この例では、クラス コンストラクターに値を割り当てる場合でも、`ChangeYear` メソッドでは `year` フィールドの値を変更できません。  
  
 [!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 `readonly` のフィールドに値の代入ができるのは、次のコンテキスト内に限られます。  
  
-   値が宣言で初期化される場合。たとえば、次のようになります。  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   インスタンス フィールドの場合は、フィールド宣言を含んでいるクラスのインスタンス コンストラクター内。静的フィールドの場合は、フィールド宣言を含んでいるクラスの静的コンストラクター内。  また、これらのコンテキスト内でだけ、`readonly` フィールドを [out](../../../csharp/language-reference/keywords/out.md) パラメーターまたは [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターとして渡すことができます。  
  
> [!NOTE]
>  `readonly` キーワードは [const](../../../csharp/language-reference/keywords/const.md) キーワードとは異なります。  `const` フィールドは、フィールドの宣言でしか初期化できません。  `readonly` フィールドは、宣言またはコンストラクターのどちらかで初期化できます。  このため、`readonly` フィールドは、使用するコンストラクターに応じて異なる値を持つことができます。  また、`const` フィールドがコンパイル時定数であるのに対し、`readonly` フィールドは実行時定数として使用できます。次に例を示します。  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## 使用例  
 [!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 上の例で、次のようにステートメントを使用するとします。  
  
 `p2.y = 66;        // Error`  
  
 次のコンパイル エラー メッセージが表示されることになります。  
  
 `The left-hand side of an assignment must be an l-value`  
  
 これは、定数に値を代入しようとしたときのエラーと同じです。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)