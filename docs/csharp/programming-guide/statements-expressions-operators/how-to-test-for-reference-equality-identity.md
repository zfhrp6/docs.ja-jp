---
title: "方法: 参照の等価性 (同値) をテストする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: 13
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
ms.openlocfilehash: a115abe599f45163c0d7e6a31dd1dab3e9c06c4b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>方法: 参照の等価性 (同値) をテストする (C# プログラミング ガイド)
独自の型で参照の等価性の比較をサポートするためにカスタム ロジックを実装する必要はありません。 この機能は、すべての型に対して <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> 静的メソッドとして用意されています。  
  
 次の例に、2 つの変数の*参照の等価性*、つまり、それらの変数がメモリ内で同一のオブジェクトを参照しているかどうかを確認する方法を示します。  
  
 また、<xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> が値型に対して常に `false` を返す理由と、文字列が等しいかどうかを確認するために <xref:System.Object.ReferenceEquals%2A> を使用しない理由を例に示します。  
  
## <a name="example"></a>例  
 [!code-cs[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 `Equals` 汎用基底クラスの <xref:System.Object?displayProperty=fullName> の実装では、参照が等しいかどうかのチェックを実行しますが、このチェックを使用しないようにお勧めします。クラスがメソッドをオーバーライドする場合、予期した結果が得られない可能性があるためです。 `==` 演算子と `!=` 演算子についても同様です。 参照型を操作しようとしている場合、== および `!=` の既定の動作では参照が等しいかどうかのチェックを実行します。 ただし、派生クラスは演算子をオーバーロードすることによって、値が等しいかどうかのチェックを実行します。 エラーが発生する可能性を最小限に抑えるために、2 つのオブジェクトの参照が等しいかどうかを確認する必要がある場合は、常に <xref:System.Object.ReferenceEquals%2A> を使用することをお勧めします。  
  
 同じアセンブリ内の定数文字列は、常に、実行時にインターンされます。 つまり、一意のリテラル文字列ごとにそのインスタンスが 1 つだけ保持されます。 ただし、ランタイムは実行時に作成された文字列がインターンされることを保証しません。また、異なるアセンブリの 2 つの等しい定数文字列がインターンされることも保証しません。  
  
## <a name="see-also"></a>関連項目  
 [等価比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)

