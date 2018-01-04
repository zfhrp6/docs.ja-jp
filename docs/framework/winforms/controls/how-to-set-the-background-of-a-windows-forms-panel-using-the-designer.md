---
title: "方法 : デザイナーを使って Windows フォーム パネルの背景を設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 995dd5982601ba92a2ec23b82acd7131db183835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>方法 : デザイナーを使って Windows フォーム パネルの背景を設定する
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールは、背景色と背景イメージの両方を表示できます。 <xref:System.Windows.Forms.Control.BackColor%2A>プロパティ パネルで、ラベルなどに含まれ、ラジオ ボタン コントロールの背景色を設定します。 場合、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティが設定されていない、<xref:System.Windows.Forms.Control.BackColor%2A>選択範囲がパネルのすべてを入力します。 場合、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティが設定されて、イメージがパネルに含まれているコントロールの内側に表示されます。  
  
 次の手順が必要です、 **Windows アプリケーション**を含むフォームを使用してプロジェクト、<xref:System.Windows.Forms.Panel>コントロール。 このようなプロジェクトを設定する方法については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Windows フォーム デザイナーの背景を設定するには  
  
1.  <xref:System.Windows.Forms.Panel> コントロールを選択します。  
  
2.  **プロパティ** ウィンドウで、矢印ボタンをクリックして、 <xref:System.Windows.Forms.Control.BackColor%2A> 3 つのタブとウィンドウを表示するプロパティです。  
  
3.  選択、**カスタム** タブの色のパレットを表示します。  
  
4.  選択、 **Web**または**システム** タブの色の定義済みの名前の一覧を表示して、色を選択します。  
  
5.  **プロパティ** ウィンドウで、矢印ボタンをクリックして、<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティです。  
  
6.  **開く** ダイアログ ボックスで、表示するファイルを選択します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Panel コントロール](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [方法: デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
