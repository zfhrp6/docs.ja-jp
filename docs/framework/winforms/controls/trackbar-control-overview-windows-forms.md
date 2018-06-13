---
title: TrackBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: d0a0cbbcc618e2fa52b3719bcc8f0135a1e0752e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535998"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.TrackBar>コントロール ("slider"コントロールと呼ばれることもあります) を使用して大量の情報内を移動するかを視覚的に数値の設定を調整します。 <xref:System.Windows.Forms.TrackBar>コントロールに 2 つの部分がある: スクロール ボックス、スライダーとティックとも呼ばれます。 つまみでは、調整可能な部分です。 その位置に対応して、<xref:System.Windows.Forms.TrackBar.Value%2A>プロパティです。 目盛りは、一定の間隔で間隔が視覚インジケーターです。 トラック バーは、増分値を指定し、水平方向または垂直方向に整列することができますをで移動します。 たとえば、トラック バーを使用して、システムのカーソルの点滅速度やマウス速度を制御する可能性があります。  
  
## <a name="key-properties"></a>キー プロパティ  
 キー プロパティ、<xref:System.Windows.Forms.TrackBar>コントロールは<xref:System.Windows.Forms.TrackBar.Value%2A>、 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>、 <xref:System.Windows.Forms.TrackBar.Minimum%2A>、および<xref:System.Windows.Forms.TrackBar.Maximum%2A>です。 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> 目盛りの間隔がします。 <xref:System.Windows.Forms.TrackBar.Minimum%2A> および<xref:System.Windows.Forms.TrackBar.Maximum%2A>トラック バーで表すことができる最小値と最大値を示します。  
  
 その他の 2 つの重要なプロパティが<xref:System.Windows.Forms.TrackBar.SmallChange%2A>と<xref:System.Windows.Forms.TrackBar.LargeChange%2A>です。 値、<xref:System.Windows.Forms.TrackBar.SmallChange%2A>プロパティは、thumb が押された左または右方向キーを持つように応答で移動するポジションの数。 値、<xref:System.Windows.Forms.TrackBar.LargeChange%2A>プロパティはつまみの PAGEUP または PAGEDOWN キーを押すへの応答を移動したり並べ替えたりマウスへの応答では、トラック バーのつまみのいずれかの側でクリックしての位置の数。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TrackBar>  
 [TrackBar コントロール](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
