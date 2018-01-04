---
title: "Windows フォーム コントロールのイベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dba74214fe439e09d1855f7ab248c075bd8257c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="events-in-windows-forms-controls"></a>Windows フォーム コントロールのイベント
Windows フォーム コントロールから 60 以上のイベントを継承する<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。 ように、<xref:System.Windows.Forms.Control.Paint>イベントは、これにより、コントロールを描画するなど、ウィンドウの表示に関連するイベント、<xref:System.Windows.Forms.Control.Resize>と<xref:System.Windows.Forms.Control.Layout>イベント、および低レベルのマウスとキーボード イベント。 一部の低レベルのイベントは、合成<xref:System.Windows.Forms.Control>ようセマンティックなイベントに<xref:System.Windows.Forms.Control.Click>と<xref:System.Windows.Forms.Control.DoubleClick>です。 継承されたイベントに関する詳細については、「<xref:System.Windows.Forms.Control>です。  
  
 継承されたイベントの機能をカスタム コントロールでオーバーライドする必要がある場合、デリゲートを結び付けるのではなく、継承された `On`*EventName* メソッドをオーバーライドします。 .NET Framework でのイベント モデルに詳しくない場合は、「[コンポーネントからのイベントの生成](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [OnPaint メソッドのオーバーライド](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [ユーザーの入力の処理](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [イベント](../../../../docs/standard/events/index.md)
