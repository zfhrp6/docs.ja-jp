---
title: '方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 3cb66aed71195d2fd2335fbd59cc499b3dbf808e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646927"
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
