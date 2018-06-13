---
title: '&#39;設定&#39;プロパティのアクセサー &#39; &lt;propertyname&gt; &#39;はアクセスできません'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: d047d03755de89d4740482db4845d5db72003ac0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595853"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;設定&#39;プロパティのアクセサー &#39; &lt;propertyname&gt; &#39;はアクセスできません
ステートメントが、プロパティへのアクセスがあるないときに、プロパティの値を格納しようとしています。`Set`プロシージャです。  
  
 場合、 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)でマークされているより制限の厳しいアクセス レベルよりもその[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)、次の場合、プロパティ値を設定しようとするが失敗します。  
  
-   `Set`ステートメントがマークされている[プライベート](../../../visual-basic/language-reference/modifiers/private.md)し、呼び出し元のコードがクラスまたはプロパティが定義されている構造体の範囲外です。  
  
-   `Set`ステートメントがマークされている[Protected](../../../visual-basic/language-reference/modifiers/protected.md)呼び出し元のコードは、派生クラスでないか、クラスまたはプロパティが定義されている構造体ではなくとします。  
  
-   `Set`ステートメントがマークされている[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)し、呼び出し元のコードは、プロパティが定義されている同じアセンブリに含まれない。  
  
 **エラー ID:** BC31102  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロパティが定義されたソース コードを使っている場合を宣言することを検討してください、`Set`プロパティ自体と同じアクセス レベルを持つプロシージャ。  
  
-   プロパティを定義するソース コードがないか、または制限する必要がある場合、`Set`プロシージャに簡単にアクセスのあるコード領域にプロパティの値を設定するコードを移動しようとしている、プロパティ自体には、複数のレベルにアクセスしますプロパティ。  
  
## <a name="see-also"></a>関連項目  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
