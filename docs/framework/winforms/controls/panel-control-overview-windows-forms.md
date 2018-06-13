---
title: Panel コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 1ba766629f923b091459531ce74d28dca4b4ea0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539350"
---
# <a name="panel-control-overview-windows-forms"></a>Panel コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.Panel>コントロールを使用して、その他のコントロールのグループに分けます。 通常、関数によって、フォームを分割するのにパネルを使用します。 たとえば、注文書を使用するどの宅配業者などの絞り込みメール配信オプションを指定するがあります。 パネルのすべてのオプションをグループ化と、ユーザーが論理を視覚的に。 デザイン時にすべてのコントロールを簡単に移動できます — を移動するとき、<xref:System.Windows.Forms.Panel>も含まれているコントロールが移動すべてを制御します。 経由でアクセスできる、コントロール パネルにグループ化されているその<xref:System.Windows.Forms.Control.Controls%2A>プロパティです。 このプロパティのコレクションを返します<xref:System.Windows.Forms.Control>ので、コントロールをキャストする必要が通常のインスタンスがその特定の型には、この方法を取得します。  
  
## <a name="panel-versus-groupbox"></a>GroupBox とパネル  
 <xref:System.Windows.Forms.Panel>コントロールに似ていますが、<xref:System.Windows.Forms.GroupBox>コントロール。 ただし、のみ、<xref:System.Windows.Forms.Panel>コントロールがスクロール バーを持つことができますのみと、<xref:System.Windows.Forms.GroupBox>コントロールは、キャプションを表示します。  
  
## <a name="key-properties"></a>主要プロパティ  
 スクロール バーを表示する設定、<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>プロパティを`true`です。 設定して、パネルの外観をカスタマイズすることも、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.BackgroundImage%2A>、および<xref:System.Windows.Forms.Panel.BorderStyle%2A>プロパティです。 詳細については、<xref:System.Windows.Forms.Control.BackColor%2A>と<xref:System.Windows.Forms.Control.BackgroundImage%2A>プロパティを参照してください[する方法: パネルの背景を設定](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)です。 <xref:System.Windows.Forms.Panel.BorderStyle%2A>プロパティは、パネルが表示されている境界のない記載されているかどうかを決定 (<xref:System.Windows.Forms.BorderStyle.None>)、普通の線 (<xref:System.Windows.Forms.BorderStyle.FixedSingle>)、またはシャドウされた行 (<xref:System.Windows.Forms.BorderStyle.Fixed3D>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Panel>  
 [GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [方法: デザイナーを使用して Windows フォーム Panel コントロールでコントロールをグループ化する](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [方法: デザイナーを使って Windows フォーム パネルの背景を設定する](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
