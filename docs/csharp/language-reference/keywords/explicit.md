---
title: "explicit (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
dev_langs:
- CSharp
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a5c842eba24f0a30d357afc24aeed10c1447345e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="explicit-c-reference"></a>explicit (C# リファレンス)
`explicit` キーワードは、キャストを使用して呼び出す必要があるユーザー定義型変換演算子を宣言します。 たとえば、次の演算子は摂氏というクラスを華氏というクラスに変換します。  
  
 [!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 この変換演算子は、次のように呼び出すことができます。  
  
 [!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 変換演算子は、ソースの型をターゲットの型に変換します。 変換演算子はソースの型によって提供されます。 暗黙的な変換とは異なり、変換演算子はキャストを使用して明示的に呼び出す必要があります。 変換操作によって例外が発生したり、情報が失われる可能性がある場合は、その操作を `explicit` としてマークする必要があります。 これにより、予期しない結果をもたらす可能性がある変換操作がコンパイラによって暗黙的に呼び出されるのを防止できます。  
  
 キャストを省略すると、コンパイル時エラー CS0266 が返されます。  
  
 詳しくは、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコードは、`Fahrenheit` クラスと `Celsius` クラスを提供する場合の例です。これらの各クラスは、他方のクラスへの明示的な変換演算子を提供します。  
  
 [!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>例  
 次のコードは、単一の 10 進数を表す構造体 (`Digit`) を定義する場合の例です。 `byte` を `Digit` に変換するための演算子が定義されていますが、すべてのバイトを `Digit` に変換できるとは限らないため、変換を explicit にしています。  
  
 [!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [implicit](../../../csharp/language-reference/keywords/implicit.md)   
 [演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)   
 [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)   
 [Chained user-defined explicit conversions in C#](http://go.microsoft.com/fwlink/?LinkId=112384) (C# でのユーザー定義の明示的変換の連結)
