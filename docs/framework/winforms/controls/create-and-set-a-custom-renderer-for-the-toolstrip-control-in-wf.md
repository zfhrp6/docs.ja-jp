---
title: "方法 : Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する | Microsoft Docs"
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
  - "例 [Windows フォーム], ツール バー"
  - "ツール バー [Windows フォーム], 描画"
  - "ToolStrip コントロール [Windows フォーム], カスタムの描画"
  - "ToolStrip コントロール [Windows フォーム], 描画"
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する
<xref:System.Windows.Forms.ToolStrip> コントロールは、テーマとスタイルを簡単に設定するための機能をサポートします。  <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> プロパティまたは <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> プロパティをカスタム レンダラーに設定すると、まったく独自の外観と操作性 \(ルック アンド フィール\) を実現できます。  
  
 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ContextMenuStrip>、または <xref:System.Windows.Forms.StatusStrip> の各コントロールに個別にレンダラーを割り当てたり、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=fullName> プロパティを <xref:System.Windows.Forms.ToolStripRenderMode?displayProperty=fullName> に設定してすべてのオブジェクトに作用する <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> プロパティを使用したりできます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> は、<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> の値が `null` ではない場合のみ、<xref:System.Windows.Forms.ToolStripRenderMode> を返します。  
  
### カスタム レンダラーを作成するには  
  
1.  <xref:System.Windows.Forms.ToolStripRenderer> クラスを拡張します。  
  
2.  適切な *On…* メンバーをオーバーライドして目的のカスタム レンダリング機能を実装します。  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
  
    ```  
  
     \[C\#\]  
  
    ```  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
  
    ```  
  
### カスタム レンダラーを現在のレンダラーとして設定するには  
  
1.  特定の<xref:System.Windows.Forms.ToolStrip> に対してカスタム レンダラーを設定するには、<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> プロパティをカスタム レンダラーに設定します。  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStrip1.Renderer = new RedTextRenderer();  
  
    ```  
  
2.  または、アプリケーションに含まれるすべての <xref:System.Windows.Forms.ToolStrip> クラスに対してカスタム レンダラーを設定するには、<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> プロパティをカスタム レンダラーに設定し、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> プロパティを <xref:System.Windows.Forms.ToolStripRenderMode> に設定します。  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>   
 <xref:System.Windows.Forms.ToolStripRenderer>   
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)