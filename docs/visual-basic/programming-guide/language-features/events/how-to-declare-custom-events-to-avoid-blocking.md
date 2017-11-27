---
title: "方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)"
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
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)
いくつかのような場合があるその 1 つのイベント ハンドラーが後続のイベント ハンドラーをブロックしない必要がある場合。 カスタム イベントは、そのイベント ハンドラーを非同期的に呼び出すイベントを許可します。  
  
 既定では、イベント宣言のバッキング ストア フィールドは、すべてのイベント ハンドラーを順番に結合したマルチキャスト デリゲートです。 つまり、1 つのハンドラーでは、完了に時間がかかる場合、ブロック、他のハンドラーが完了するまでです。 (正常に動作するイベント ハンドラーは、時間のかかるまたはブロックしている可能性がある操作を実行する必要があることはありません)。  
  
 Visual Basic が提供するイベントの既定の実装を使用する代わりに、イベント ハンドラーを非同期的に実行するのにカスタム イベントを使用することができます。  
  
## <a name="example"></a>例  
 この例では、`AddHandler`アクセサーは、の各ハンドラーのデリゲートを追加、`Click`イベントを<xref:System.Collections.ArrayList>に格納されている、`EventHandlerList`フィールドです。  
  
 ときにコードが発生し、`Click`イベント、`RaiseEvent`アクセサーが非同期的を使用してすべてのイベント ハンドラーのデリゲートを呼び出す、<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>メソッドです。 そのメソッドでは、ワーカー スレッドで各ハンドラーが呼び出され、ハンドラーが互いをブロックできませんので、すぐに返します。  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [方法: カスタム イベントを宣言してメモリを節約する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
