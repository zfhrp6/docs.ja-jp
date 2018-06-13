---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 414998b4bef526060e7ba4f584fa071fbd0acaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595876"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Visual Basic で宣言されている外部プロシージャの外部名に基づいて、.NET Framework の規則に従って文字列をマーシャ リングする必要がありますを指定します。  
  
 プロジェクト外で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラにはプロシージャを正しく呼び出すために必要な情報へのアクセスはありません。 この情報には、プロシージャが配置されている、それを識別する方法、その呼び出しシーケンスおよび戻り値の型が含まれます。 および使用する文字列の文字セットします。 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、この必要な情報を提供します。  
  
 `charsetmodifier`の一部、`Declare`ステートメントが外部プロシージャの呼び出し中に文字列をマーシャ リングするための文字セットの情報を提供します。 Visual Basic が外部プロシージャ名を外部ファイルを検索する方法にも影響します。 `Auto`修飾子は、Visual Basic が、.NET Framework の規則に従って文字列をマーシャ リングし、おり、場合、ランタイム プラットフォームの設定の基本文字を決定する必要があります最初の検索する場合、外部プロシージャ名を変更する必要がありますを指定します。失敗します。 詳細についてを参照してください「の文字セット」 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)です。  
  
 文字セットに修飾子が指定されていない場合`Ansi`既定値です。  
  
## <a name="remarks"></a>コメント  
 `Auto`修飾子は、このコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 このキーワードはサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)
