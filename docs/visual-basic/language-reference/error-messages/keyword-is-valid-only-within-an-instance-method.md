---
title: '&#39;&lt;キーワード&gt;&#39;はインスタンス メソッド内でのみ有効です'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586361"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;&lt;キーワード&gt;&#39;はインスタンス メソッド内でのみ有効です
`Me`、 `MyClass`、および`MyBase`キーワードは、特定のクラスのインスタンスを参照してください。 共有内には使用できません`Function`または`Sub`プロシージャです。  
  
 **エラー ID:** BC30043  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャからキーワードを削除するか、削除、`Shared`プロシージャ宣言からキーワード。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数の代入](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
