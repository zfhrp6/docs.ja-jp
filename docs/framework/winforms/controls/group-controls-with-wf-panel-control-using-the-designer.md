---
title: "方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], グループ化"
  - "Panel コントロール [Windows フォーム], グループ化 (コントロールを)"
  - "Windows フォーム コントロール, グループ化"
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する
Windows フォームの <xref:System.Windows.Forms.Panel> コントロールを使用すると、他のコントロールをグループ化できます。  コントロールのグループ化には、次の 3 つの利点があります。  まず、関連しているフォーム要素を視覚的にグループ化し、わかりやすいユーザー インターフェイスを提供できます。また、オプション ボタンなどをグループ化してプログラミングできます。さらに、デザイン時に複数のコントロールをまとめて移動できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールのグループを作成するには  
  
1.  ツールボックスの **\[Windows フォーム\]** タブから、<xref:System.Windows.Forms.Panel> コントロールをフォームにドラッグします。  
  
2.  パネルにほかのコントロールを追加し、パネル内に各コントロールを配置します。  
  
     既存のコントロールをパネルに追加する場合は、追加するすべてのコントロールを選択し、クリップボードに切り取ります。次に、<xref:System.Windows.Forms.Panel> コントロールを選択し、そのコントロールをパネルに貼り付けます。  コントロールをパネルにドラッグすることもできます。  
  
3.  \(省略可能\) パネルに境界線を追加する場合は、<xref:System.Windows.Forms.BorderStyle> プロパティで設定します。  <xref:System.Windows.Forms.BorderStyle>、<xref:System.Windows.Forms.BorderStyle>、および <xref:System.Windows.Forms.BorderStyle> という 3 つの選択項目があります。  
  
## 参照  
 [Panel コントロール](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [方法 : パネルの背景を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)