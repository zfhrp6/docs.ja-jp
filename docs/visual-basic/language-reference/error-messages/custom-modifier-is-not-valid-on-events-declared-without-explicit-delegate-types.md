---
title: "&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31122"
  - "bc31122"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31122"
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Custom&#39; modifier is not valid on events declared without explicit delegate types
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

非カスタム イベントとは異なり、`Custom Event`の宣言では、イベントのデリゲート型を明示的に指定する `As` 句をイベント名の後に指定する必要があります。  
  
 非カスタム イベントであれば、`As` 句と明示的なデリゲート型を指定するか、またはイベント名のすぐ後にパラメーター リストを指定することで定義できます。  
  
 **Error ID:** BC31122  
  
### このエラーを解決するには  
  
1.  カスタム イベントと同じパラメーター リストを指定してデリゲートを定義します。  
  
     たとえば、`Custom Event`が `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` で定義されている場合、対応するデリゲートの定義は次のようになります。  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/custom-modifier-is-not-v_1.vb)]  
  
2.  カスタム イベントのパラメーター リストを、デリゲート型を指定する `As` 句で書き換えます。  
  
     先の例を使用すると、`Custom Event`の宣言は次のように書き換えられます。  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/custom-modifier-is-not-v_2.vb)]  
  
## 使用例  
 次の例は、`Custom Event` を宣言して、必須である `As` 句をデリゲート型と一緒に指定します。  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/custom-modifier-is-not-v_3.vb)]  
  
## 参照  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)