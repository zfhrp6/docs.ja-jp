---
title: "方法 : TableLayoutPanel コントロールの列と行を編集する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf54a02a409bead598a4e98315d5709e55677f3b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>方法 : TableLayoutPanel コントロールの列と行を編集する
コレクション エディターを使用することができます、<xref:System.Windows.Forms.TableLayoutPanel>と呼ばれるコントロール、**列と行のスタイル**ダイアログ ボックスで、行と、コントロールの列を編集します。  
  
> [!NOTE]
>  を複数の行または列の span を制御する場合は、設定、`RowSpan`と`ColumnSpan`コントロールのプロパティです。 詳細については、「 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)」を参照してください。  
>   
>  セル内のコントロールを配置する場合、またはセル内で stretch を制御する場合は、使用、コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティです。 詳細については、「 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-edit-rows-and-columns"></a>行と列を編集するには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
2.  クリックして、<xref:System.Windows.Forms.TableLayoutPanel>コントロールのスマート タグ グリフ (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) を選択して**編集行と列**を開くには、 **列と行のスタイル** ダイアログ ボックス。 右クリックで、<xref:System.Windows.Forms.TableLayoutPanel>してコントロールを選択**編集行と列**ショートカット メニューからです。  
  
3.  列を追加または削除、選択**列**から、**メンバー型**ドロップダウン リスト ボックス。  
  
4.  追加したり、行を削除する選択**行**から、**メンバー型**ドロップダウン リスト ボックス。  
  
5.  クリックして、**追加**の末尾に行または列を追加するボタン、**メンバー**  ボックスの一覧です。  
  
6.  をクリックして、**挿入**一覧で行または現在選択されている項目の前に列を追加するボタンをクリックします。  
  
7.  行または列を追加する場合は、選択、**サイズの種類**新しい行または列に対応します。 詳細については、「<xref:System.Windows.Forms.SizeType>」を参照してください。  
  
8.  行または列を削除する をクリックして、**削除**で現在選択されている項目を削除するボタン、**メンバー**  ボックスの一覧です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.SizeType>  
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
