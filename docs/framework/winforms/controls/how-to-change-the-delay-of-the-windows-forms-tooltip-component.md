---
title: '方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 20dcd941b142daa672312edb618a1c3e4597442d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530430"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する
Windows フォームに設定できる複数の遅延時間の値がある<xref:System.Windows.Forms.ToolTip>コンポーネントです。 これらすべてのプロパティの単位はミリ秒です。 <xref:System.Windows.Forms.ToolTip.InitialDelay%2A>プロパティは、ユーザーに関連付けられているコントロールに表示されるツールヒント文字列を指す必要があります期間を決定します。 <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>プロパティは、後続のツールヒント文字列が表示されるツールヒントに関連付けられている 1 つのコントロール間、マウスを移動するまでのミリ秒数を設定します。 <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>プロパティは、ツール ヒントの文字列が表示される時間の長さを指定します。 これらの値を設定するには、個別またはの値を設定して、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>プロパティ; に割り当てられている値に基づいてプロパティが設定の他の遅延、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>プロパティです。 たとえば、 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> N の値に設定されている<xref:System.Windows.Forms.ToolTip.InitialDelay%2A>N」に設定されている<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>の値に設定されている<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>5 で割った値 (または N/5) と<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>5 倍の値を示す値に設定されている、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>プロパティ (または 5N)。  
  
### <a name="to-set-the-delay"></a>遅延を設定するには  
  
1.  この例で示すように、次のプロパティを設定します。  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>関連項目  
 [ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [方法: デザイン時に Windows フォームのコントロールにツールヒントを設定する](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
