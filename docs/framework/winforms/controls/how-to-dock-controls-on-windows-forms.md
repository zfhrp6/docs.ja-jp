---
title: '方法 : Windows フォーム上のコントロールをドッキングする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532324"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>方法 : Windows フォーム上のコントロールをドッキングする
コントロールをフォームの端にドッキングするか、またはコントロールのコンテナー (フォームまたはコンテナー コントロール) を挿入したりします。 Windows エクスプ ローラーのドッキングなど、その<xref:System.Windows.Forms.TreeView>ウィンドウの左側にあるコントロールとその<xref:System.Windows.Forms.ListView>ウィンドウの右側にあるコントロールです。 使用して、<xref:System.Windows.Forms.Control.Dock%2A>すべて表示されている Windows フォームのコントロールのドッキングのモードを定義するプロパティです。  
  
> [!NOTE]
>  逆の z オーダーでコントロールがドッキングされます。  
  
 <xref:System.Windows.Forms.Control.Dock%2A>プロパティの対話、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。 詳細については、次を参照してください。 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)です。  
  
### <a name="to-dock-a-control"></a>コントロールのドッキング  
  
1.  ドッキングするコントロールを選択します。  
  
2.  [プロパティ] ウィンドウの右側にある矢印をクリックして、<xref:System.Windows.Forms.Control.Dock%2A>プロパティです。  
  
     一連の端と、フォームの中央を表すボックスを示す、エディターが表示されます。  
  
3.  コントロールをドッキングするフォームの端を表すボタンをクリックします。 コントロールのフォームまたはコンテナー コントロールの内容を入力するには、中央のボックスをクリックします。 をクリックして **(なし)** ドッキングを無効にします。  
  
     コントロールがドッキングされた端の境界に合わせてサイズに自動的に変更します。  
  
    > [!NOTE]
    >  継承されたコントロールがある必要があります`Protected`ドッキングできるようにします。 コントロールのアクセス レベルを変更するには、次のように設定します。 その**修飾子**プロパティ ウィンドウでプロパティです。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [方法: Windows フォームにコントロールを固定する](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
