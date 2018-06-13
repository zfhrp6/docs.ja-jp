---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: a61fd8e10c39569d92dd84180f678a1ff05a9310
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595723"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Visual Basic には、宣言されている外部プロシージャの名前に関係なく、Unicode の値にすべての文字列がマーシャ リングを指定します。  
  
 プロジェクト外で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラには、プロシージャを正しく呼び出すために必要があります情報へのアクセスはありません。 この情報には、プロシージャが配置されている、それを識別する方法、その呼び出しシーケンスおよび戻り値の型が含まれます。 および使用する文字列の文字セットします。 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、この必要な情報を提供します。  
  
 `charsetmodifier`の一部、`Declare`ステートメントは、外部プロシージャの呼び出し中に文字列をマーシャ リングには、文字セットの情報を提供します。 Visual Basic が外部プロシージャ名を外部ファイルを検索する方法にも影響します。 `Unicode`修飾子は、Visual Basic がすべての文字列を Unicode 値のマーシャ リングする必要があり、検索中にその名前を変更することがなく、プロシージャを検索する必要がありますを指定します。  
  
 文字セットに修飾子が指定されていない場合`Ansi`既定値です。  
  
## <a name="remarks"></a>コメント  
 `Unicode`修飾子は、このコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 このキーワードはサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)
