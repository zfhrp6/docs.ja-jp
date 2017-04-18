---
title: "&quot;Custom&quot; 修飾子は、明示的なデリゲート型なしで宣言されたイベントに対して無効な |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0e70fca6a0608df5db43156f70196b4e5c9b2339
ms.lasthandoff: 03/13/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' 修飾子は、明示的なデリゲート型なしで宣言されたイベントでは無効
非カスタム イベントとは異なり、`Custom Event`宣言が必要ですが`As`句を次に示す、イベントのデリゲート型を明示的に指定するイベントの名前。  
  
 非カスタム イベントは、いずれかで定義されている、`As`句と明示的なデリゲート型、またはすぐにパラメーターを持つリスト イベント名の後です。  
  
 **エラー ID:** BC31122  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  カスタム イベントと同じパラメーター リストを持つデリゲートを定義します。  
  
     たとえば場合、`Custom Event`で定義された`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`、対応するデリゲートは、次です。  
  
     [!code-vb[VbVbalrEventError&#18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  カスタム イベントとのパラメーターのリストを置き換える、`As`デリゲート型を指定する句。  
  
     先ほどの例では、`Custom Event`宣言を次のように書き換えることができます。  
  
     [!code-vb[VbVbalrEventError&#19;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>例  
 この例で宣言、`Custom Event`し、必要な指定`As`デリゲート型を含む句。  
  
 [!code-vb[VbVbalrEventError&#2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
