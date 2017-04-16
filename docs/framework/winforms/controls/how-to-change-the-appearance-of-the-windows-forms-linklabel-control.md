---
title: "方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する | Microsoft Docs"
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
  - "例 [Windows フォーム], LinkLabel コントロール"
  - "LinkLabel コントロール [Windows フォーム], 変更 (リンクの表示形式を)"
  - "LinkLabel コントロール [Windows フォーム], 例"
  - "LinkLabel のプロパティ"
  - "リンク, 変更 (表示形式を)"
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する
<xref:System.Windows.Forms.LinkLabel> によって表示されるテキストは、さまざまな目的に合わせて変更できます。  たとえば、テキストに下線を付けて特定の色で表示されるように設定することにより、このテキストをクリックできることをユーザーに示します。  ユーザーがテキストをクリックすると、テキストは別の色に変わります。  この動作は、<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>、<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>、および <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> という 5 つの異なるプロパティを設定して制御できます。  
  
### LinkLabel コントロールの表示形式を変更するには  
  
1.  <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> プロパティと <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> プロパティに適切な色を設定します。  
  
     この処理は、プログラム実行時に行うことも、デザイン時に **\[プロパティ\]** ウィンドウで行うこともできます。  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2.  <xref:System.Windows.Forms.LinkLabel.Text%2A> プロパティに適切なキャプションを設定します。  
  
     この処理は、プログラム実行時に行うことも、デザイン時に **\[プロパティ\]** ウィンドウで行うこともできます。  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティを設定して、キャプションのどの部分をリンクとして表示するかを指定します。  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> の値は、<xref:System.Windows.Forms.LinkArea> で表されます。このオブジェクトには、文字の開始位置と文字数を示す 2 つの数字が含まれます。  この処理は、プログラム実行時に行うことも、デザイン時に **\[プロパティ\]** ウィンドウで行うこともできます。  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> プロパティを <xref:System.Windows.Forms.LinkBehavior>、<xref:System.Windows.Forms.LinkBehavior>、または <xref:System.Windows.Forms.LinkBehavior> に設定します。  
  
     このプロパティを <xref:System.Windows.Forms.LinkBehavior> に設定している場合は、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティで指定したキャプションの一部にマウス ポインターを置いた場合にだけ下線が付けられます。  
  
5.  <xref:System.Windows.Forms.LinkLabel.LinkClicked> イベント ハンドラー内で、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> プロパティを `true` に設定します。  
  
     既にアクセス済みのリンクは、なんらかの方法で外観が変更されます。通常はリンクの色が変更されます。  テキストが <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> プロパティで指定した色に変わります。  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>   
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>   
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>   
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>   
 [LinkLabel コントロールの概要](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)   
 [方法 : Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)   
 [LinkLabel コントロール](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)