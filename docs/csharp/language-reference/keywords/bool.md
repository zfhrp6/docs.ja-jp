---
title: "bool (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ef8cc9a0584829eeed06e7fc3c2227f0683ef413
ms.lasthandoff: 03/13/2017

---
# <a name="bool-c-reference"></a>bool (C# リファレンス)
`bool` キーワードは、<xref:System.Boolean?displayProperty=fullName> の別名です。 ブール値 ([true](../../../csharp/language-reference/keywords/true.md) と [false](../../../csharp/language-reference/keywords/false.md)) を格納する変数を宣言するために使われます。  
  
> [!NOTE]
>  値 `null` も格納できるブール変数が必要な場合は、`bool?` を使います。 詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
## <a name="literals"></a>リテラル  
 `bool` 変数にはブール値を代入できます。 また、`bool` として評価される式も `bool` 変数に代入できます。  
  
 [!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 `bool` 変数の既定値は `false` です。 `bool?` 変数の既定値は `null` です。  
  
## <a name="conversions"></a>変換  
 C++ では、`bool` 型の値を `int` 型の値に変換できます。つまり、`false` はゼロと同等であり、`true` はゼロ以外の値と同等です。 C# では、`bool` 型と他の型の間に変換はありません。 たとえば、次の `if` ステートメントは C# では無効です。  
  
 [!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 `int` 型の変数をテストするには、0 などの値と明示的に比較する必要があります。次はその例です。  
  
 [!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>例  
 この例のプログラムは、キーボードから文字された文字がアルファベットかどうかを調べます。 アルファベットである場合は、小文字か大文字かを調べます。 これらのチェックは、<xref:System.Char.IsLetter%2A> と <xref:System.Char.IsLower%2A> で実行されます。どちらも、`bool` 型を返します。  
  
 [!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
