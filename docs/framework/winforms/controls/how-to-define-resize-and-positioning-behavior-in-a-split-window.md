---
title: "方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "分割ウィンドウ, サイズ変更"
  - "SplitContainer コントロール [Windows フォーム], サイズ変更"
  - "分割ウィンドウ, サイズ変更"
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する
<xref:System.Windows.Forms.SplitContainer> コントロールのパネルは、ユーザーがサイズ変更や操作を行う場合にたいへん役立ちます。  しかし、分割線を配置する場所や分割線を移動できる程度について、プログラムで分割線を制御する場合もあります。  
  
 <xref:System.Windows.Forms.SplitContainer> コントロールの <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティなどのプロパティを使用すると、必要に応じてユーザー インターフェイスの動作を正確に制御できます。  これらのプロパティについては次の表に示します。  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> プロパティ|キーボードまたはマウスによって分割線が移動できるかどうかを決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> プロパティ|左端または上端から移動できる分割バーまでの距離 \(ピクセル単位\) を決定します。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティ|ユーザーが分割線を移動できる最小距離 \(ピクセル単位\) を決定します。|  
  
 次の例では、<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティを変更して、"分割線のスナップ" 効果を作り出します。ユーザーが分割線をドラッグすると、既定値の 1 ピクセルではなく、10 ピクセル単位で値が増加します。  
  
### SplitContainer コントロールのサイズ変更動作を定義するには  
  
1.  プロシージャで、分割線の "スナップ" 動作が得られるように、<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> プロパティに必要な値を設定します。  
  
     次のコード例では、フォームの <xref:System.Windows.Forms.Form.Load> イベント内で、<xref:System.Windows.Forms.SplitContainer> コントロール内の分割線がドラッグ時に 10 ピクセル単位でジャンプするように設定されています。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     分割線を左右に少しだけ移動しても、目に見える効果はありません。しかし、マウス ポインターをどちらかの方向に 10 ピクセル移動すると、分割線が新しい位置にスナップします。  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>