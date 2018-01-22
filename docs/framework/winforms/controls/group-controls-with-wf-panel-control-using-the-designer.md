---
title: "方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1c6dd45d2070c77b34c66388b397bb784215654
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールを使用すると、その他のコントロールをグループ化します。 コントロールをグループ化の 3 つの理由があります。 視覚的にわかりやすいユーザー インターフェイスです。 関連するフォーム要素のグループ化もう 1 つは、プログラムによるグループ化、ラジオ ボタンの例を示します。最後は、デザイン時に単位として、コントロールを移動です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-a-group-of-controls"></a>コントロールのグループを作成するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.Panel>から制御、 **Windows フォーム**からフォームにツールボックス タブをクリックします。  
  
2.  パネル内の各描画、パネルには、その他のコントロールを追加します。  
  
     パネルにする既存のコントロールがあれば、すべてのコントロールを選択して、それらを選択、クリップボードに切り取れません、<xref:System.Windows.Forms.Panel>を制御して、パネルに貼り付けます。 パネルにドラッグすることもできます。  
  
3.  (省略可能)パネルに罫線を追加する場合は、設定、<xref:System.Windows.Forms.BorderStyle>プロパティです。 次の 3 つの選択肢があります: <xref:System.Windows.Forms.BorderStyle.Fixed3D>、 <xref:System.Windows.Forms.BorderStyle.FixedSingle>、および<xref:System.Windows.Forms.BorderStyle.None>です。  
  
## <a name="see-also"></a>参照  
 [Panel コントロール](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [方法: パネルの背景を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
