---
title: "value (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
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
ms.openlocfilehash: de1106994ec513e27bf3c6a011e905684fcd41af
ms.lasthandoff: 03/13/2017

---
# <a name="value-c-reference"></a>value (C# リファレンス)
コンテキスト キーワード `value` は、set アクセサーの通常のプロパティ宣言で使用します。 これは、メソッドの入力パラメーターに似ています。 `value` というキーワードは、クライアント コードでプロパティに割り当てる値を表します。 次の例の `MyDerivedClass` には、`Name` というプロパティがあります。このプロパティは `value` パラメーターを使用して、バッキング フィールド `name` に新しい文字列を割り当てます。 クライアント コードから見ると、演算は簡単な代入演算として記述されます。  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 `value` の使用に関する詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
