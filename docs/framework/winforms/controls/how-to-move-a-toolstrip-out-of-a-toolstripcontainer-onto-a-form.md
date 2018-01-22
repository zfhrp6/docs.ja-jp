---
title: "方法 : ToolStrip を ToolStripContainer からフォームに移動する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97d65abf38ee434218fa9bec0d8a9cade31fb687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>方法 : ToolStrip を ToolStripContainer からフォームに移動する
移動する、次の手順を使用して、<xref:System.Windows.Forms.ToolStrip>のうち、<xref:System.Windows.Forms.ToolStripContainer>からフォームにします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>ToolStrip を ToolStripContainer からフォームに不足を移動するには  
  
1.  <xref:System.Windows.Forms.ToolStrip> を選択します。  
  
2.  切り取り、<xref:System.Windows.Forms.ToolStrip>で ctrl キーを押しながら X キーを押すかを右クリックし、<xref:System.Windows.Forms.ToolStrip>選択**切り取り**コンテキスト メニューからです。  
  
3.  フォームを選択します。  
  
4.  貼り付け、<xref:System.Windows.Forms.ToolStrip>で ctrl キーを押しながら V キーを押すかを選択して**貼り付け**から、**編集**メニュー。  
  
5.  設定、<xref:System.Windows.Forms.ToolStrip.Dock%2A>のプロパティ、<xref:System.Windows.Forms.ToolStrip>に**上部**です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
