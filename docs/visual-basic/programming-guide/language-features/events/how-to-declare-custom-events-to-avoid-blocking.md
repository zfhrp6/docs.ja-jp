---
title: "方法: (Visual Basic の場合) がブロックされないようにするカスタム イベントを宣言する |Microsoft ドキュメント"
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
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
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
ms.openlocfilehash: 34b222bdbfdae0673b7150c220ca477b7e286dda
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)
その&1; つのイベント ハンドラーが後続のイベント ハンドラーをブロックしない重要な場合は、いくつかの状況にもあります。 カスタム イベントは、そのイベント ハンドラーを非同期的に呼び出すイベントを許可します。  
  
 既定では、イベント宣言のバッキング ストア フィールドは、すべてのイベント ハンドラーを順番に結合したマルチキャスト デリゲートです。 これは、1 つのハンドラーに完了までに時間がある場合は、パラメーターを妨げる他のハンドラーが完了するまでことを意味します。 (正常に動作するイベント ハンドラーは、時間のかかる処理を妨げる可能性のある操作を実行する必要があることはありません) します。  
  
 Visual Basic ではイベントの既定の実装を使用する代わりに、イベント ハンドラーを非同期的に実行するのにカスタム イベントを使用できます。  
  
## <a name="example"></a>例  
 この例では、`AddHandler`アクセサーは、の各ハンドラーのデリゲートを追加、`Click`イベントを<xref:System.Collections.ArrayList>に格納されている、`EventHandlerList`フィールド</xref:System.Collections.ArrayList>。  
  
 コードを発生させるのと、 `Click` 、イベント、`RaiseEvent`アクセサーが非同期的を使用してすべてのイベント ハンドラーのデリゲートを呼び出す、<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>メソッド</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>。 そのメソッドでは、ワーカー スレッドで各ハンドラーが呼び出され、ハンドラーは、互いをブロックできませんので、すぐに返します。  
  
 [!code-vb[VbVbalrEvents #&27;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.ArrayList></xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [方法: カスタム イベントを宣言してメモリを節約する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
