---
title: "方法 : ToolStrip コントロールをカスタム描画する | Microsoft Docs"
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
  - "カスタム描画"
  - "描画, カスタム"
  - "描画, オーナー"
  - "例 [Windows フォーム], ツール バー"
  - "オーナー描画"
  - "ProfessionalColorTable クラス, オーバーライド"
  - "RenderMode プロパティ"
  - "ツール バー [Windows フォーム], 変更 (色を)"
  - "ツール バー [Windows フォーム], カスタム描画"
  - "ToolStrip コントロール [Windows フォーム], 変更 (色を)"
  - "ToolStrip コントロール [Windows フォーム], 描画"
  - "ToolStripProfessionalRenderer クラス"
  - "ToolStripRenderer クラス"
  - "ToolStripRenderMode クラス"
  - "ToolStripSystemRenderer クラス"
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ToolStrip コントロールをカスタム描画する
<xref:System.Windows.Forms.ToolStrip> コントロールに、次のレンダリング \(描画\) クラスが関連付けられています。  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> は、オペレーティング システムの外観とスタイルを提供します。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> は、Microsoft Office の外観とスタイルを提供します。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> は、その他の 2 つのレンダリング クラスの抽象基本クラスです。  
  
 <xref:System.Windows.Forms.ToolStrip> をカスタムで描画 \(オーナー描画\) するために、レンダラー クラスの 1 つをオーバーライドして表示ロジックの特定の側面を変更できます。  
  
 次の手順は、カスタムの描画のさまざまな側面について説明します。  
  
### 設定されているレンダラー間で切り替えるには  
  
-   <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> プロパティを任意の <xref:System.Windows.Forms.ToolStripRenderMode> の値に設定します。  
  
     <xref:System.Windows.Forms.ToolStripRenderMode> と共に、静的な <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> がアプリケーションのレンダラーを決定します。  <xref:System.Windows.Forms.ToolStripRenderMode> のその他の値は、<xref:System.Windows.Forms.ToolStripRenderMode>、<xref:System.Windows.Forms.ToolStripRenderMode>、および <xref:System.Windows.Forms.ToolStripRenderMode> です。  
  
### Microsoft Office スタイルの境界を直線に変更するには  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=fullName> をオーバーライドしますが、基本クラスは呼び出しません。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripSystemRenderer>、および <xref:System.Windows.Forms.ToolStripProfessionalRenderer> に対して、このメソッドのバージョンがあります。  
  
### ProfessionalColorTable を変更するには  
  
-   <xref:System.Windows.Forms.ProfessionalColorTable> をオーバーライドして必要な色を変更します。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
  
    ```  
  
### アプリケーション内のすべての ToolStrip コントロールのレンダリングを変更するには  
  
1.  <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=fullName> プロパティを使用して、設定されているレンダラーのいずれかを選択します。  
  
2.  <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> を使用して、カスタム レンダラーを割り当てます。  
  
3.  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=fullName> が既定値の <xref:System.Windows.Forms.ToolStripRenderMode> に設定されていることを確認します。  
  
### アプリケーション全体で Microsoft Office の色をオフにするには  
  
-   <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=fullName> を `false` に設定します。  
  
### 1 つの ToolStrip コントロールで Microsoft Office の色をオフにするには  
  
-   次のコード例に似たコードを使用します。  
  
     \[Visual Basic\]  
  
    ```  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
  
    ```  
  
     \[C\#\]  
  
    ```  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>   
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>   
 <xref:System.Windows.Forms.ToolStripRenderer>   
 [組み込みのオーナー描画サポートを備えたコントロール](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)   
 [方法 : Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)