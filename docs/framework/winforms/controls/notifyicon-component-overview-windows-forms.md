---
title: "NotifyIcon コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d951d45232437026cc41d8e40284207ea1c64ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、通常、バックグラウンドで動作し、ユーザー インターフェイスに長時間表示されないプロセスのアイコンを表示する場合に使用されます。 たとえば、タスク バーの状態通知領域のアイコンをクリックしてアクセス可能なウイルス対策プログラムなどです。  
  
## <a name="key-properties-of-notifyicons"></a>NotifyIcons のキー プロパティ  
 各 <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、ステータス領域に 1 つのアイコンを表示します。 3 つのバック グラウンド プロセスがあり、それぞれのアイコンを表示する必要がある場合は、3 つの <xref:System.Windows.Forms.NotifyIcon> コンポーネントをフォームに追加する必要があります。 <xref:System.Windows.Forms.NotifyIcon> コンポーネントのキー プロパティは、<xref:System.Windows.Forms.NotifyIcon.Icon%2A> および <xref:System.Windows.Forms.NotifyIcon.Visible%2A> です。 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> プロパティは、ステータス領域に表示されるアイコンを設定します。 アイコンを表示するために、<xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティを `true` に設定する必要があります。  
  
 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] を使用している場合は、<xref:System.Windows.Forms.NotifyIcon> コントロールによって使用できる標準のイメージの大規模なライブラリにアクセスできます。  
  
## <a name="notifyicons-options"></a>NotifyIcons オプション  
 バルーン ヒント、ショートカット メニュー、およびツールヒントを <xref:System.Windows.Forms.NotifyIcon> に関連付けて、ユーザーを支援できます。  
  
 <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> メソッドを呼び出して、バルーンヒントを表示する期間を指定することで、<xref:System.Windows.Forms.NotifyIcon> のバルーン ヒントを表示できます。 テキスト、アイコン、およびとバルーン ヒントのタイトルを、それぞれ <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>、<xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A>、および <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A> を使用して指定できます。 <xref:System.Windows.Forms.NotifyIcon> コンポーネントには、ツールヒントとショートカット メニューも関連付けることができます。 詳細については、次を参照してください。 [ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)と[ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.NotifyIcon>  
 [NotifyIcon コンポーネント](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
