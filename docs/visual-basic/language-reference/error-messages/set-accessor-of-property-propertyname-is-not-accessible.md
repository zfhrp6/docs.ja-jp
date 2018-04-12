---
title: '&#39;です。セット &#39;プロパティ &#39; アクセサー&lt;propertyname&gt;&#39; にアクセスできません'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;です。セット &#39;プロパティ &#39; アクセサー&lt;propertyname&gt;&#39; にアクセスできません
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
