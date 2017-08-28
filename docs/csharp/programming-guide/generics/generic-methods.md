---
title: "ジェネリック メソッド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: 27
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
ms.openlocfilehash: 14461773303bafc098f79c3686b1f76827f11005
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generic-methods-c-programming-guide"></a>ジェネリック メソッド (C# プログラミング ガイド)
ジェネリック メソッドは、次のように型パラメーターで宣言されるメソッドです。  
  
 [!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 メソッドの呼び出し方法の 1 つを示しているのが次のコード サンプルです。型引数に `int` を利用します。  
  
 [!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 型引数は省略することもできます。コンパイラが推定します。 次は、前の呼び出しと同じように `Swap` を呼び出します。  
  
 [!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 型推定の同じ規則が静的メソッドとインスタンス メソッドに適用されます。 コンパイラは、渡されたメソッド引数に基づいて型パラメーターを推定できます。制約や戻り値だけでは型パラメーターを推定できません。 そのため、パラメーターのないメソッドでは型を推定できません。 型はコンパイル時に、コンパイラがオーバーロードされたメソッド シグネチャを解決する前に推定されます。 コンパイラは、同じ名前を共有するすべてのジェネリック メソッドに型の推定ロジックを適用します。 オーバーロード解決手順では、型を推定できたジェネリック メソッドのみがコンパイラに含まれます。  
  
 ジェネリック クラス内では、非ジェネリック メソッドは、次のように、クラスレベルの型パラメーターにアクセスできます。  
  
 [!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 包含クラスと同じ型パラメーターを受け取るジェネリック メソッドを定義すると、コンパイラは警告 CS0693 を生成します。これは、メソッド範囲内で、内側の `T` に与えられた引数により外側の `T` に与えられた引数が隠されるためです。 クラスがインスタンス化されたときに与えらたれ型パラメーター以外の型パラメーターでジェネリック クラス メソッドを呼び出すという柔軟性が必要な場合、メソッドの型パラメーターに別の識別子を指定することを検討してください。次の例の `GenericList2<T>` をご覧ください。  
  
 [!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 メソッドの型パラメーターでさらに多くの特殊操作を可能にするために、制約を使用します。 `SwapIfGreater<T>` という名前が付けられた `Swap<T>` のこのバージョンは、<xref:System.IComparable%601> を実装する型引数との併用でのみ利用できます。  
  
 [!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 ジェネリック メソッドは、いくつかの型パラメーターでオーバーロードできます。 たとえば、次のメソッドはすべて同じクラスに配置できます。  
  
 [!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 詳細については、「[C# 言語の仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)

