---
title: "方法 : デザイナーで Windows フォーム TabControl を使ってタブを追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e603e420be2c5be6174fab3876008fdf73c8459
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a>方法 : デザイナーで Windows フォーム TabControl を使ってタブを追加および削除する
配置するとき、<xref:System.Windows.Forms.TabControl>コントロール フォームで、既定では 2 つのタブがあります。 追加するか、デザイナーを使用してタブを削除します。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.TabControl>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a>追加またはデザイナーを使用して、タブを削除するには  
  
-   コントロールのスマート タグでは、をクリックして**タブの追加**または**タブの削除**  
  
     - または -  
  
     **プロパティ**ウィンドウで、をクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティを開くには、 **TabPage コレクション エディター**です。 クリックして、**追加**または**削除**ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [方法: タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [方法: タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [方法: Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
