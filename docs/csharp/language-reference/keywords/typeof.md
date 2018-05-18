---
title: typeof (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: be79fa4f2cfb1119a50201bf6c18a144726f2f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="typeof-c-reference"></a>typeof (C# リファレンス)
型の `System.Type` オブジェクトを取得するために使用されます。 `typeof` 式は次の形式になります。  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>コメント  
 式の実行時の型を取得する場合は、次の例のように、.NET Framework のメソッド <xref:System.Object.GetType%2A> を使用できます。  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` 演算子はオーバーロードできません。  
  
 `typeof` 演算子は、オープン ジェネリック型に対しても使用できます。 複数の型パラメーターを持つ型には、適切な数のコンマを指定する必要があります。 次の例は、メソッドの戻り値の型がジェネリック <xref:System.Collections.Generic.IEnumerable%601> であるかどうかを確認する方法を示しています。 ここでは、メソッドが MethodInfo 型のインスタンスであると仮定します。  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>例  
 このサンプルでは、<xref:System.Object.GetType%2A> メソッドを使用して、数値計算結果の格納に使用される型を確認しています。 これは、結果の数のストレージ要件によって変わります。  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Type?displayProperty=nameWithType>  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)
