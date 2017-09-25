---
title: "delegate (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
dev_langs:
- CSharp
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 402eedd0c59b5c95e1a9b44faca66ccb4d4e04e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="delegate-c-reference"></a>delegate (C# リファレンス)
デリゲート型の宣言は、メソッド シグネチャに似ています。 戻り値 1 つのほか、任意の型のパラメーターをいくつでも指定することができます。  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 `delegate` は、名前付きメソッドまたは匿名メソッドをカプセル化することができる参照型です。 デリゲートは C++ の関数ポインターに似ていますが、タイプ セーフであり安全です。 デリゲートの使い方については、[デリゲート](../../../csharp/programming-guide/delegates/index.md)と[汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)に関するページを参照してください。  
  
## <a name="remarks"></a>コメント  
 デリゲートは[イベント](../../../csharp/programming-guide/events/index.md)の土台となる働きをします。  
  
 デリゲートは名前付きメソッドまたは匿名メソッドに関連付けることによって、インスタンス化することができます。 詳細については、[名前付きメソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)と[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)に関するページを参照してください。  
  
 デリゲートは、適合する入力パラメーターと戻り値の型を持ったメソッドまたはラムダ式でインスタンス化する必要があります。 メソッドのシグネチャでどの程度の変性が許容されるかについて詳しくは、[デリゲートの変性](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)に関するページを参照してください。 匿名メソッドで使用する場合は、デリゲートとそれに関連付けるコードとを一緒に宣言します。 このセクションでは、その両方の方法でデリゲートをインスタンス化しています。  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [名前付きメソッドを使用したデリゲートと匿名メソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)   
 [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)

