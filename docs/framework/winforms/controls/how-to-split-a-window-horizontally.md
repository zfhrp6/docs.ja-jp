---
title: "方法 : ウィンドウを水平方向に分割する | Microsoft Docs"
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
  - "SplitContainer コントロール [Windows フォーム], 水平分割線"
  - "分割ウィンドウ, 変更 (分割線の向きを)"
  - "分割ウィンドウ, 水平"
  - "ウィンドウ, 分割 (水平方向に)"
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : ウィンドウを水平方向に分割する
<xref:System.Windows.Forms.SplitContainer> コントロールを水平方向に分割する分割線を作成するコード例を次に示します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SplitContainer> コントロールの <xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティは、コントロール自体の方向ではなく、分割線の方向を指定します。  
  
### ウィンドウを水平方向に分割するには  
  
1.  プロシージャ内で、<xref:System.Windows.Forms.SplitContainer> コントロールの <xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティに <xref:System.Windows.Forms.Orientation> を設定します。  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)