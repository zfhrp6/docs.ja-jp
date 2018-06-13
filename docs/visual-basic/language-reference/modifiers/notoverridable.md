---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600754"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
プロパティまたはプロシージャを派生クラスでオーバーライドできないことを指定します。  
  
## <a name="remarks"></a>コメント  
 `NotOverridable`修飾子プロパティまたはメソッドが派生クラスでオーバーライドされないできなくなります。  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)修飾子により、派生クラスでオーバーライドするクラスでプロパティまたはメソッドです。 詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 場合、`Overridable`または`NotOverridable`修飾子が指定されていない、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。 プロパティまたはメソッドは、基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定値は`Overridable`です。 それ以外の場合は`NotOverridable`します。  
  
 上書きできないように要素と呼ぶことが、*シール*要素。  
  
 `NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 指定できます`NotOverridable`プロパティまたはとの組み合わせでのみ、つまり、別のプロパティまたはプロシージャをオーバーライドするプロシージャでのみ`Overrides`です。  
  
## <a name="combined-modifiers"></a>結合された修飾子  
 指定することはできません`Overridable`または`NotOverridable`の`Private`メソッドです。  
  
 指定することはできません`NotOverridable`と共に`MustOverride`、 `Overridable`、または`Shared`同じ宣言内で。  
  
## <a name="usage"></a>使用法  
 `NotOverridable` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [修飾子](../../../visual-basic/language-reference/modifiers/index.md)  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
