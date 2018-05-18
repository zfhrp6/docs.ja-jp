---
title: '方法: Null 許容型を識別する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f3ac4ebd77fc92a133eb326919d5ba55264ced97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>方法: Null 許容型を識別する (C# プログラミング ガイド)
C# の [typeof](../../../csharp/language-reference/keywords/typeof.md) 演算子を使用して、Null 許容型を表す <xref:System.Type> オブジェクトを作成することができます。  
  
```  
System.Type type = typeof(int?);  
```  
  
 <xref:System.Reflection> 名前空間のクラスおよびメソッドを使用して、Null 許容型を表す <xref:System.Type> オブジェクトを作成することもできます。 ただし、実行時に <xref:System.Object.GetType%2A> メソッドまたは `is` 演算子を使用して Null 許容型の変数から型情報を取得しようとすると、Null 許容型自体ではなく、基になる型を表す <xref:System.Type> オブジェクトが作成されます。  
  
 Null 許容型に対して `GetType` を呼び出すと、型が暗黙的に <xref:System.Object> に変換されるときに、ボックス化操作が実行されます。 そのため、<xref:System.Object.GetType%2A> は常に、Null 許容型ではなく、基になる型を表す <xref:System.Type> オブジェクトを返します。  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C# の [is](../../../csharp/language-reference/keywords/is.md) 演算子も Null 許容型の基になる型に作用します。 そのため、変数が Null 許容型であるかどうかを判別する際に `is` を使用することはできません。 次の例は、`is` 演算子が Nullable\<int> 変数を int として処理することを示しています。  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>例  
 次のコードを使用して、<xref:System.Type> オブジェクトが Null 許容型を表しているかどうかを判別します。 このトピックで前述したように、`Type` オブジェクトが <xref:System.Object.GetType%2A> の呼び出しから返された場合、このコードは常に false を返します。  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>参照  
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
 [Null 許容型のボックス化](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
