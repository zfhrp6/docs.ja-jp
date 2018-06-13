---
title: Default (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: 555e15110c7af501de05d1f395a72ca4b7800054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595146"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
そのクラス、構造体、またはインターフェイスの既定のプロパティとしてプロパティを識別します。  
  
## <a name="remarks"></a>コメント  
 クラス、構造体、またはインターフェイスを指定できますとそのプロパティの 1 つ、*既定プロパティ*プロパティは、少なくとも 1 つのパラメーターを受け取りますが、します。 コードでは、クラスまたは構造体への参照をメンバーを指定しなくても、Visual Basic は、既定のプロパティには、その参照を解決します。  
  
 既定のプロパティは、ソース コードの文字のわずかな低下につながるが行えるコード読みにくくなります。 クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合は指定できません特定その参照が、クラスまたは構造体自体、または既定のプロパティにアクセスするかどうか。 これは、コンパイラ エラーまたは実行時の微妙な論理エラーを可能性があります。  
  
 常を使用して既定のプロパティのエラーの可能性を低くことができます多少、 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)をチェックインするコンパイラ タイプを設定する`On`です。  
  
 使用を計画して、定義済みのクラスまたは構造体、コード内を決定する必要がありますを既定のプロパティがあるかどうかと、その場合、どのような名前です。  
  
 これらの欠点のためには、既定のプロパティを定義しないを検討してください。 コードの読みやすさも常にすべてのプロパティを明示的に参照を検討も既定のプロパティする必要があります。  
  
 `Default`修飾子は、このコンテキストで使用できます。  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)
