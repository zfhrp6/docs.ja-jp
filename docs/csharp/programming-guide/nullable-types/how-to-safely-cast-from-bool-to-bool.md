---
title: "方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: 9
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
ms.openlocfilehash: c8a3dc3280b7dca802b327d9454c7f0ba9ed44be
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)
Null 許容 `bool?` 型は、`true`、`false`、`null` の 3 つの異なる値を格納できます。 そのため、`bool?` 型は、`if`、`for`、`while` などの条件文で使用できません。 たとえば、次のコードはコンパイラ エラーになります。  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 コンパイルできないのは、条件文のコンテキストで `null` の意味があいまいだからです。 条件付きステートメントで `bool?` を使用するにはまず、その <xref:System.Nullable%601.HasValue%2A> プロパティをチェックしてその値が `null` でないことを確認します。次に、`bool` にキャストします。 詳細については、「[bool](../../../csharp/language-reference/keywords/bool.md)」を参照してください。 `bool?` でキャストを実行するときに値が `null` になっていると、条件テストで <xref:System.InvalidOperationException> がスローされます。 次の例は、`bool?` から `bool` に安全にキャストするための 1 つの方法を示しています。  
  
## <a name="example"></a>例  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [リテラル キーワード](../../../csharp/language-reference/keywords/literal-keywords.md)   
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [??演算子](../../../csharp/language-reference/operators/null-conditional-operator.md)

