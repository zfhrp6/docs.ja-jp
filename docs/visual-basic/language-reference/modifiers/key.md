---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92d54e3135142bc02a17f3ce5ac078a356c139be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599845"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key`キーワードでは、匿名型のプロパティの動作を指定することができます。 匿名型のインスタンス、またはハッシュ コード値の計算の間の等値に関するテストでキー プロパティとしてを指定したプロパティのみです。 キー プロパティの値を変更することはできません。  
  
 キー プロパティとして、キーワードを配置することで、匿名型のプロパティを指定する`Key`初期化リストでその宣言の前にします。 次の例では、`Airline`と`FlightNo`キーのプロパティが`Gate`はありません。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 新しい匿名型を作成すると、する場合から直接継承<xref:System.Object>です。 コンパイラは、次の 3 つの継承されたメンバーをオーバーライドします。 <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>です。 オーバーライド コードの生成される<xref:System.Object.Equals%2A>と<xref:System.Object.GetHashCode%2A>キー プロパティに基づきます。 型のキー プロパティがない場合<xref:System.Object.GetHashCode%2A>と<xref:System.Object.Equals%2A>はオーバーライドされません。  
  
## <a name="equality"></a>等価比較  
 同じ型のインスタンスと、主要なプロパティの値が等しい場合、匿名型の 2 つのインスタンスが等しい。 次の例についてで`flight2`と等しい`flight1`前の例から、同じ匿名のインスタンスがいるため、型と、一致している、キー プロパティの値。 ただし、`flight3`は等しくありません`flight1`キーのプロパティの値が異なるため`FlightNo`です。 インスタンス`flight4`と同じ型ではない`flight1`キー プロパティとしてさまざまなプロパティを指定するためです。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 プロパティを持つのみ非キー、名前、種類、順序、および値で、同じ 2 つのインスタンスが宣言されている場合は 2 つのインスタンスが等しくありません。 キー プロパティを指定せず、インスタンス自体にのみ等価です。  
  
 匿名型の 2 つのインスタンスを同じ匿名型のインスタンスである条件の詳細については、次を参照してください。[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)です。  
  
## <a name="hash-code-calculation"></a>ハッシュ コードの計算  
 同様に<xref:System.Object.Equals%2A>、ハッシュ関数で定義されている<xref:System.Object.GetHashCode%2A>匿名型は、型のキー プロパティに基づく。 次の例は、コードの値にハッシュ キーのプロパティ間の相互作用を示します。  
  
 すべてのキー プロパティに対して同じ値を持つ匿名型のインスタンスでは、非キー プロパティに一致する値があるない場合でも、同じハッシュ コード値があります。 次のステートメントから`True`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 1 つまたは複数のキー プロパティに別の値を持つ匿名型のインスタンスでは、別のハッシュ コード値があります。 次のステートメントから`False`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 キー プロパティとしてさまざまなプロパティを指定する匿名型のインスタンスは、同じ型のインスタンスではありません。 名前とすべてのプロパティの値が同じ場合でも、別のハッシュ コード値があります。 次のステートメントから`False`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>読み取り専用の値  
 キー プロパティの値を変更することはできません。 たとえば、`flight1`前の例で、`Airline`と`FlightNo`フィールドは読み取り専用が`Gate`変更できます。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 [匿名型の定義](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
