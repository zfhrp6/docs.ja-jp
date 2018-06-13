---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 5dabd90d29bc41d017436876af24a67fa87e8e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599871"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
プロパティまたはプロシージャは、このクラスで実装されていませんしを使用する前に、派生クラスでオーバーライドする必要がありますを指定します。  
  
## <a name="remarks"></a>コメント  
 `MustOverride` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 プロパティまたはプロシージャを指定する`MustOverride`クラスのメンバーである必要があります、クラスをマークする必要がありますと[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **不完全な宣言です。** 指定すると`MustOverride`、プロパティまたはプロシージャのコードの追加線をできません指定しないであっても、 `End Function`、 `End Property`、または`End Sub`ステートメントです。  
  
-   **結合された修飾子。** 指定することはできません`MustOverride`と共に`NotOverridable`、 `Overridable`、または`Shared`同じ宣言内で。  
  
-   **シャドウとオーバーライドされます。** シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。 詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)です。  
  
-   **代替の条件です。** オーバーライドで以外は使用できませんを要素と呼ぶことが、*純粋仮想*要素。  
  
 `MustOverride` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
