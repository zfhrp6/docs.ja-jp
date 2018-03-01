---
title: "Windows フォームにおけるマウスのキャプチャ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cc62780579c852aaa637a3ccc13ce2929423868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Windows フォームにおけるマウスのキャプチャ
*マウスのキャプチャ*コントロールは、すべてのマウス入力のコマンドを実行する場合を参照します。 コントロールがマウスをキャプチャしていた場合は、ポインターが境界内にあるかどうかを示す、マウス入力を受け取ります。  
  
## <a name="setting-mouse-capture"></a>マウスのキャプチャの設定  
 Windows フォームでは、ユーザーがコントロールでマウス ボタンを押すし、ユーザーがマウス ボタンを離すと、マウスがコントロールによってリリースされたときに、マウスがコントロールによってキャプチャされます。  
  
 <xref:System.Windows.Forms.Control.Capture%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラスは、コントロールがマウスをキャプチャしたかどうかを指定します。 調べるには、コントロールがマウス キャプチャを失ったときに、処理、<xref:System.Windows.Forms.Control.MouseCaptureChanged>イベント。  
  
 前面のウィンドウのみでは、マウスをキャプチャできます。 バック グラウンド ウィンドウがマウスをキャプチャしようとすると、ウィンドウは、ウィンドウの表示部分内でマウス ポインターがあるときに発生するマウス イベントのメッセージだけを受け取ります。 また、場合でも、前面のウィンドウは、マウスをキャプチャして、ユーザーでもはクリックして別のウィンドウが前面に取り込みます。 マウスがキャプチャされると、ショートカット キーは機能しません。  
  
## <a name="see-also"></a>参照  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
