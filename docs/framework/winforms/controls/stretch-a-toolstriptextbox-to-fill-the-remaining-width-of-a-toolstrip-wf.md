---
title: '方法 : ToolStripTextBox を拡大して ToolStrip の残りの幅に合わせる (Windows フォーム)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: bd58cbd109b8e3dd04c6a284dc6926e95830fb61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537721"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>方法 : ToolStripTextBox を拡大して ToolStrip の残りの幅に合わせる (Windows フォーム)
設定すると、<xref:System.Windows.Forms.ToolStrip.Stretch%2A>のプロパティ、<xref:System.Windows.Forms.ToolStrip>に制御を`true`コントロールのコンテナーをエンド ツー エンドで塗りつぶし、コンテナーのサイズを変更すると、サイズ変更します。 この構成では有用なことなど、コントロールでは、項目をストレッチする、<xref:System.Windows.Forms.ToolStripTextBox>空き領域の塗りつぶし、およびコントロールのサイズを変更するとサイズ変更します。 この拡大役に立ちます、たとえば、外観と Microsoft® Internet Explorer のアドレス バーのような動作を実現したい場合。  
  
## <a name="example"></a>例  
 次のコード例から派生したクラスを提供する<xref:System.Windows.Forms.ToolStripTextBox>と呼ばれる`ToolStripSpringTextBox`です。 このクラスは、オーバーライド、<xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>親の使用可能な幅を計算するメソッド<xref:System.Windows.Forms.ToolStrip>他のすべての項目の幅の合計を削除した後に制御します。 このコード例も提供、<xref:System.Windows.Forms.Form>クラスおよび`Program`クラスに新しい動作を示します。  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [方法: StatusStrip 内で Spring プロパティを対話的に使用する](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
