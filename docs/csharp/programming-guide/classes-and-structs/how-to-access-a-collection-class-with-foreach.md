---
title: "方法: foreach を使用してコレクション クラスにアクセスする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
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
ms.openlocfilehash: 2ad81ab699b079f4aabb04a886211e94a937335d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a>方法: foreach を使用してコレクション クラスにアクセスする (C# プログラミング ガイド)
次のコード例では、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) で使用できる非ジェネリック コレクション クラスを記述する方法を示しています。 この例では、文字列トークナイザー クラスを定義します。  
  
> [!NOTE]
>  この例では、汎用のコレクション クラスを使用できないときのみに推奨される方法を示します。 <xref:System.Collections.Generic.IEnumerable%601> をサポートするタイプ セーフの汎用的なコレクション クラスを実装する方法の例は、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」を参照してください。  
  
 この例では、次のコード セグメントが `Tokens` クラスを使用し、"This is a sample sentence." という文を  ' ' と '-' の区切りを使用してトークンに分割しています。 その後、コードでは `foreach` ステートメントを使用し、それらのトークンを示します。  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>例  
 `Tokens` クラスは、内部でトークンの保存に配列を使用します。 配列は <xref:System.Collections.IEnumerator> と <xref:System.Collections.IEnumerable> を実装するため、このコード例では、`Tokens` クラスで定義する代わりに、配列の列挙メソッド (<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A>、<xref:System.Collections.IEnumerator.Current%2A>) を使用することができました。 その定義方法およびそれらの動作を示すために、例にはメソッドの定義が含まれています。  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 C# の場合、<xref:System.Collections.IEnumerable> と <xref:System.Collections.IEnumerator> を実装しなくてもコレクション クラスは `foreach` 互換になります。 クラスに必須の <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A>、<xref:System.Collections.IEnumerator.Current%2A> メンバーがある場合、`foreach` と連動します。 インターフェイスを省略すると、<xref:System.Object> よりも限定的な `Current` 用の戻り値の型を定義することが可能になると言う利点があります。 これにより、タイプ セーフとなります。  
  
 たとえば、前の例の下記の行を変更します。  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 `Current` では、文字列を返すので、`foreach` ステートメントで互換性のない型が使用されたとき、コンパイラが次のコードのとおりそれを検出できます。  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <xref:System.Collections.IEnumerable> と <xref:System.Collections.IEnumerator> を省略した場合、コレクション クラスが `foreach` ステートメント、同等のステートメントや他の共通言語ランタイム言語と互換性がなくなるという欠点があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)

