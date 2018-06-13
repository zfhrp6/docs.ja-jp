---
title: デリゲート クラス&#39; &lt;classname&gt; &#39;この型の式はメソッドの呼び出しのターゲットにすることはできませんので Invoke メソッドがありません
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: cc1abba46224772e733780800dd104dfc7ebe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588831"
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>デリゲート クラス&#39; &lt;classname&gt; &#39;この型の式はメソッドの呼び出しのターゲットにすることはできませんので Invoke メソッドがありません
呼び出し`Invoke`がデリゲートから失敗しました。`Invoke`デリゲート クラスで実装されていません。  
  
 **エラー ID:** BC30220  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  デリゲート クラスのインスタンスが作成されたことを確認してください、`Dim`ステートメントと、プロシージャがデリゲートのインスタンスに割り当てられている、`AddressOf`演算子。  
  
2.  デリゲート クラスを実装するコードを検索しを実装するかどうかを確認、`Invoke`プロシージャです。  
  
## <a name="see-also"></a>関連項目  
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
