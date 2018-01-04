---
title: "方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed78a49119c87c52a07cc2ade030e66087d3f420
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する
パネル、<xref:System.Windows.Forms.SplitContainer>コントロール役立つ中に適切にサイズ変更され、ユーザーが操作されます。 ただしがあるプログラムから分割線を制御する場合は、場所が配置されているしにどの程度まで移動できます。  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>プロパティおよびその他のプロパティを<xref:System.Windows.Forms.SplitContainer>コントロールは、ニーズに合わせて、ユーザー インターフェイスの動作を正確に制御を提供します。 これらのプロパティは、次の表に一覧表示されます。  
  
|name|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティ|分割線は、キーボードまたはマウスを使用して移動可能なかどうかを判断します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティ|移動可能な分割バーを左端または上端からのピクセル単位で距離を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティ|最小の距離 (ピクセル単位)、スプリッターをユーザーが移動できることを決定します。|  
  
 次の例を変更、 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 「スナップ分割」効果; を作成するプロパティの既定値 1 ではなく、10 のピクセル単位で増加、ユーザーが分割線をドラッグしたとき。  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>SplitContainer のサイズ変更動作を定義するには  
  
1.  プロシージャでは、設定、<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>プロパティ、希望するサイズを 'スナップ' スプリッターの動作を実現できるようにします。  
  
     フォームの内で、次のコード例で<xref:System.Windows.Forms.Form.Load>イベント、内のスプリッター、<xref:System.Windows.Forms.SplitContainer>コントロールにドラッグすると、10 のピクセルのジャンプに設定します。  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     左または右にスプリッターを若干移動効果はありません難しくします。ただし、マウス ポインターが両方向に 10 ピクセルに出ると、分割が新しい位置にスナップされます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
