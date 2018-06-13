---
title: '方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647203"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)
いくつかのような場合があること、アプリケーションのメモリ使用量を低く抑える必要がある場合。 カスタム イベントでは、アプリケーションが、処理するイベントに対してだけメモリを使用できるようにします。  
  
 既定では、クラスは、イベントを宣言すると、コンパイラは、イベント情報を格納するフィールドのメモリを割り当てます。 場合は、クラスには未使用のイベントが多く、不必要にメモリを受け取ります。  
  
 Visual Basic が提供するイベントの既定の実装を使用する代わりに、メモリ使用量をより慎重に管理するのにカスタム イベントを使用することができます。  
  
## <a name="example"></a>例  
 この例では 1 つのインスタンスを使用するクラス、<xref:System.ComponentModel.EventHandlerList>で格納されているクラス、`Events`使用中のイベントに関する情報を格納するためのフィールドです。 <xref:System.ComponentModel.EventHandlerList>クラスは、最適化された一覧クラスにデリゲートを保持するために設計されています。  
  
 クラスの使用中のすべてのイベント、`Events`どのような方法で各イベントが処理を追跡するフィールドです。  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.EventHandlerList>  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [方法: カスタム イベントを宣言してブロックを回避する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
