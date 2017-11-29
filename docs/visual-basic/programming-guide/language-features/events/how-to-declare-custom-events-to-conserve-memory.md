---
title: "方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eec9a2fc687f481ab40313e35cbde81c25b81ae8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
