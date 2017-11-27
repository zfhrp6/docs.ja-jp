---
title: "配列の変換 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a>配列の変換 (Visual Basic)
別の配列型、配列型を変換するには、次の条件を満たしていれば。  
  
-   **ランクが等しい。** 2 つの配列のランクは同じである必要があります、つまり、同じ次元数がある必要があります。 ただし、それぞれの次元の長さが同じにする必要はありません。  
  
-   **要素のデータ型。** 両方の配列の要素のデータ型は、参照型である必要があります。 変換することはできません、`Integer`配列を`Long`配列、またはにも、`Object`に少なくとも 1 つの値の型が関係するための配列。 詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)です。  
  
-   **変換可能性です。** 変換、拡張または縮小は、2 つの配列の要素の型の間でできる必要があります。 この要件に失敗した例は、の間で変換しようとする`String`配列とクラスの配列から派生した<xref:System.Attribute?displayProperty=nameWithType>です。 これらの 2 種類 nothing に共通あり、それらの間に任意の種類の変換が存在しないです。  
  
 1 つの配列型の間の変換は、拡大または自動それぞれの要素の変換を拡大または縮小するかどうかに応じて縮小します。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## <a name="conversion-to-an-object-array"></a>オブジェクトの配列への変換  
 宣言する場合、`Object`初期化せず、要素の型の配列が`Object`それが初期化されていない限りです。 を特定のクラスの配列を設定するとそのクラスの型になります。 しかし、基になる型は`Object`、関連のないクラスの別の配列を後で設定できます。 すべてのクラスを派生させるため`Object`、任意のクラス、配列の要素の型を変更するには、他のクラスです。  
  
 次の例では、変換が存在しない型の間で`student`と`String`から派生して両方`Object`ので、すべての割り当てが無効です。  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>基になる、配列の型  
 特定のクラスを含む配列を宣言していた場合は、そのクラスは、基になる要素の種類です。 設定した場合、後で別のクラスの配列を 2 つのクラス間の変換が必要があります。  
  
 次の例では、`students`は、`student`配列。 間で変換が存在しないため`String`と`student`、最後のステートメントは失敗します。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [方法: オブジェクトを Visual Basic での別の型に変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
