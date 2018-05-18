---
title: ジェネリック インターフェイス (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 72f48aa1d70e6cf81b20adc547e2d418c4497256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="generic-interfaces-c-programming-guide"></a>ジェネリック インターフェイス (C# プログラミング ガイド)
ジェネリック コレクション クラスのインターフェイスか、コレクション内の項目を表すジェネリック クラスのインターフェイスを定義すると、多くの場合、便利です。 ジェネリック クラスの優先設定の意図は、値型に対するボックス化とボックス化解除を回避する目的で、<xref:System.IComparable> ではなく <xref:System.IComparable%601> など、ジェネリック インターフェイスを利用することにあります。 .NET Framework クラス ライブラリにより、<xref:System.Collections.Generic> 名前空間のコレクション クラスと共に利用するためのジェネリック インターフェイスがいくつか定義されます。  
  
 インターフェイスが型パラメーターの制約として指定される場合、インターフェイスを実装する型のみを利用できます。 `GenericList<T>` クラスから派生する `SortedList<T>` クラスを示したのが次のコード サンプルです。 詳細については、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。 `SortedList<T>` により制約 `where T : IComparable<T>` が追加されます。 これにより、`SortedList<T>` の `BubbleSort` メソッドは、一覧要素でジェネリック <xref:System.IComparable%601.CompareTo%2A> メソッドを利用できます。 この例では、一覧要素は単純なクラスである `Person` です。これは `IComparable<Person>` を実装します。  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 次のように、複数のインターフェイスを単一の型で制約として指定できます。  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 1 つのインターフェイスで、次のように、複数の型パラメーターを定義できます。  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 クラスに適用される継承規則は、インターフェイスにも適用されます。  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 ジェネリック インターフェイスが反変の場合、つまり、その型パラメーターを戻り値としてのみ利用する場合、ジェネリック インターフェイスは非ジェネリック インターフェイスから継承できます。 .NET Framework クラス ライブラリでは、<xref:System.Collections.Generic.IEnumerable%601> は <xref:System.Collections.IEnumerable> から継承します。これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> の戻り値と <xref:System.Collections.Generic.IEnumerator%601.Current%2A> プロパティ ゲッターの `T` のみを利用するためです。  
  
 具象クラスは、次のように、構築されたクローズ型インターフェイスを実装できます。  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 ジェネリック クラスは、クラス パラメーターの一覧からインターフェイスが必要とするすべての引数が提供される限り、ジェネリック インターフェイスや構築されたクローズ型インターフェイスを実装できます。  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 メソッドのオーバーロードを制御する規則は、ジェネリック クラス、ジェネリック構造体、ジェネリック インターフェイス内のメソッドの規則と同じです。 詳細については、「[ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
 [ジェネリック](~/docs/standard/generics/index.md)
