---
title: "params (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5999911b96d17c710096e74c8f3da65223e778fc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="params-c-reference"></a>params (C# リファレンス)
`params` キーワードを使用すると、可変数個の引数を受け取る[メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)を指定できます。  
  
 パラメーター宣言で指定した型の引数のコンマ区切りのリスト、または指定した型の引数の配列を渡すことができます。 また、引数を渡さないこともできます。 引数を渡さない場合、`params` リストの長さはゼロになります。  
  
 1 つのメソッド宣言内では、`params` キーワード以後にパラメーターを追加できないため、1 つの `params` キーワードだけを使用できます。  
  
## <a name="example"></a>例  
 次の例に示すように、さまざまな方法で `params` パラメーターに引数を渡すことができます。  
  
 [!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)

