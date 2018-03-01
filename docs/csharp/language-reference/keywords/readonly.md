---
title: "readonly (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b499f9fc5121afe6c2e92bcf8c5d2ac593b4c06c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-c-reference"></a>readonly (C# リファレンス)
`readonly` キーワードは、フィールドで使用できる修飾子です。 フィールド宣言に `readonly` 修飾子が含まれていると、その宣言によって導入されるフィールドへの割り当ては、宣言の一部分として、または同じクラスのコンストラクター内でのみ実行できます。  
  
## <a name="example"></a>例  
 この例では、`year` フィールドの値は、クラス コンストラクターで値が割り当てられていても `ChangeYear` メソッドでは変更できません。  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 `readonly` のフィールドに値を割り当てることができるのは、次のコンテキスト内に限られます。  
  
-   値が宣言で初期化される場合。次に例を示します。  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   インスタンス フィールドの場合は、フィールド宣言が含まれるクラスのインスタンス コンストラクター内。静的フィールドの場合は、フィールド宣言が含まれるクラスの静的コンストラクター内。 また、こうしたコンテキスト内でのみ、`readonly` フィールドを [out](../../../csharp/language-reference/keywords/out.md) パラメーターまたは [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターとして渡すことができます。  
  
> [!NOTE]
>  `readonly` キーワードは [const](../../../csharp/language-reference/keywords/const.md) キーワードとは異なります。 `const` フィールドは、フィールドの宣言でしか初期化できません。 `readonly` フィールドは、宣言またはコンストラクターのどちらかで初期化できます。 このため、`readonly` フィールドは、使用するコンストラクターに応じて異なる値を持つことができます。 また、次の例のように、`const` フィールドがコンパイル時定数であるのに対し、`readonly` フィールドは実行時定数として使用できます。  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 上の例で、次のようにステートメントを使用するとします。  
  
 `p2.y = 66;        // Error`  
  
 この場合、次のコンパイル エラー メッセージが表示されます。  
  
 `The left-hand side of an assignment must be an l-value`  
  
 これは、定数に値を割り当てようとしたときのエラーと同じです。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)
