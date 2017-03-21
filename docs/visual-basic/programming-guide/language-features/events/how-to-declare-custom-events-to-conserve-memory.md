---
title: "方法: (Visual Basic) のメモリを節約するためにカスタム イベントを宣言する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 4f8ce32a3b4da411a73010119283ce9661b82a6c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)
いくつかのような場合があること、アプリケーションのメモリ使用量を低く抑える必要がある場合。 カスタム イベントを使うアプリケーションが、処理するイベントに対してだけメモリを使用します。  
  
 既定では、クラスは、イベントを宣言すると、コンパイラは、イベント情報を格納するフィールドのメモリを割り当てます。 クラスの未使用のイベントが多くの場合、不要なメモリを消費します。  
  
 Visual Basic ではイベントの既定の実装を使用する代わりに、メモリ使用量をより注意深く管理するのにカスタム イベントを使用できます。  
  
## <a name="example"></a>例  
 この例では、クラスが&1; つのインスタンスを使用して、<xref:System.ComponentModel.EventHandlerList>に格納されているクラス、`Events`使用中のイベントに関する情報を格納するためのフィールド</xref:System.ComponentModel.EventHandlerList>。 <xref:System.ComponentModel.EventHandlerList>クラスは、最適化されたリスト クラスのデリゲートを保持するために設計されています</xref:System.ComponentModel.EventHandlerList>。  
  
 クラス使用中のすべてのイベント、`Events`どのような方法には、各イベントが処理を追跡するフィールドです。  
  
 [!code-vb[VbVbalrEvents #&22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList>   
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [方法: カスタム イベントを宣言してブロックを回避する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
