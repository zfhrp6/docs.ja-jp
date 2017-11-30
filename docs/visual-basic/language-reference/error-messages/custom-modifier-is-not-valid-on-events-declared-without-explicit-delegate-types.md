---
title: "&#39;です。カスタム &#39;修飾子は無効です。 明示的なデリゲート型なしで宣言されたイベント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords: BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;です。カスタム &#39;修飾子は無効です。 明示的なデリゲート型なしで宣言されたイベント
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
