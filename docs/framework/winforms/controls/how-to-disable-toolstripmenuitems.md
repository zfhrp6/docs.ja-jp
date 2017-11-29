---
title: "方法 : ToolStripMenuItems を無効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3307da3e0810ea775c799a4b065e1f7484b5779
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-toolstripmenuitems"></a>方法 : ToolStripMenuItems を無効にする
制限またはを有効にして、ユーザー アクティビティを応答でのメニュー項目を無効にすると、ユーザーが実行できるコマンドの範囲を広げることができます。 メニュー項目は既定で有効には、作成されるが、これで調整できる場合に、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティです。 デザイン時にこのプロパティを操作することができます、**プロパティ**ウィンドウまたはプログラムによってコードで設定します。  
  
### <a name="to-disable-a-menu-item-programmatically"></a>メニュー項目をプログラムで無効にするには  
  
-   メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`です。  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  メニューの最初または最上位レベルのメニュー項目を無効にすると、メニュー内に含まれるすべてのメニュー項目を非表示が、それらを無効にしません。 同様に、サブメニュー項目を持つメニュー項目を無効にするサブメニュー項目を非表示が、それらを無効にしません。 指定されたメニュー上のすべてのコマンドがユーザーに利用可能な場合は、この場合は、クリーンなユーザー インターフェイスとして両方を非表示にし、メニュー全体を無効にすることをお勧めプログラミングと見なされます。 非表示にする、メニューを無効にして単独で非表示にする場合、アクセスのショートカット キーを使用してメニュー コマンドにあるために、すべてのアイテムと、メニューのサブメニュー項目を無効にしてください。 設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>をトップレベルのメニュー項目のプロパティ`false`メニュー全体を非表示にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [方法: ToolStripMenuItems を非表示にする](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
