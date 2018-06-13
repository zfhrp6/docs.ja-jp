---
title: '&#39;カスタム&#39;modifier は明示的なデリゲート型なしで宣言されたイベントでは有効ではありません'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587522"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;カスタム&#39;modifier は明示的なデリゲート型なしで宣言されたイベントでは有効ではありません
非カスタム イベントとは異なり、`Custom Event`宣言が必要です、`As`句が次のイベントの名前を明示的にイベントのデリゲート型を指定します。  
  
 非カスタム イベントを指定できますいずれかで定義されている、`As`句と、明示的なデリゲート型、またはすぐにパラメーターを持つリスト次のイベントの名前。  
  
 **エラー ID:** BC31122  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  カスタム イベントとして同じパラメーター リストを持つデリゲートを定義します。  
  
     たとえば場合、`Custom Event`によって定義された`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`を対応するデリゲートは、次です。  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  カスタム イベントのパラメーター一覧の置換、`As`句のデリゲート型を指定します。  
  
     この例では、`Custom Event`宣言を次のように書き換えることができます。  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>例  
 この例で宣言、`Custom Event`し、必要な指定`As`デリゲート型を含む句。  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
