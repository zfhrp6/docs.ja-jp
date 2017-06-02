---
title: "partial (型) (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
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
ms.openlocfilehash: 29cec1546de1058929ec192614bc460a9df176ce
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="partial-type-c-reference"></a>partial (型) (C# リファレンス)
部分型定義では、クラス、構造体、またはインターフェイスの定義を複数のファイルに分割することができます。  
  
 次に File1.cs の部分型定義を示します。  
  
 [!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 次に File2.cs での宣言を示します。  
  
 [!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a>コメント  
 クラス型、構造体型、またはインターフェイス型を複数のファイルに分割する操作は、大規模なプロジェクトや、[Windows フォーム デザイナー](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)で自動生成されるコードを処理する場合に役立ちます。 部分型には、[部分メソッド](../../../csharp/language-reference/keywords/partial-method.md)が含まれる場合があります。 詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)
