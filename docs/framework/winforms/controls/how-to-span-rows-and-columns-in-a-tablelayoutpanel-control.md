---
title: "方法 : TableLayoutPanel コントロールの行と列を拡大する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e29db51401edccf57aa89307a159efc28eb1d4da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>方法 : TableLayoutPanel コントロールの行と列を拡大する
コントロールで、<xref:System.Windows.Forms.TableLayoutPanel>コントロールが隣接する行と列にまたがることができます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-span-columns-and-rows"></a>列と行にまたがること  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
2.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
3.  設定、<xref:System.Windows.Forms.Button>コントロールの**ColumnSpan**プロパティを**2**です。 なお、<xref:System.Windows.Forms.Button>コントロールが最初と 2 番目の列にまたがってです。  
  
4.  設定、<xref:System.Windows.Forms.Button>コントロールの**RowSpan**プロパティを**2**です。 なお、<xref:System.Windows.Forms.Button>コントロールの最初と 2 番目の行にまたがって表示します。  
  
5.  設定、<xref:System.Windows.Forms.Button>コントロールの**ColumnSpan**プロパティを**1**です。 なお、<xref:System.Windows.Forms.Button>コントロールは、最初の列に移動し、最初と 2 番目の行にまたがるです。  
  
## <a name="see-also"></a>参照  
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
