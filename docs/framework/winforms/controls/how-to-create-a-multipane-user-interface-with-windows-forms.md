---
title: "方法 : Windows フォームでマルチペイン ユーザー インターフェイスを作成する | Microsoft Docs"
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
  - "ListView コントロール [Windows フォーム], 例"
  - "Panel コントロール [Windows フォーム], 例"
  - "RichTextBox コントロール [Windows フォーム], 例"
  - "SplitContainer コントロール [Windows フォーム], 例"
  - "Splitter コントロール [Windows フォーム], 例"
  - "TreeView コントロール [Windows フォーム], 例"
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 方法 : Windows フォームでマルチペイン ユーザー インターフェイスを作成する
次の手順では、Microsoft Outlook で使用されているユーザー インターフェイスに似た**フォルダー**一覧、**メッセージ** ペイン、および**プレビュー** ペインを備えたマルチペイン ユーザー インターフェイスを作成します。  これは、主にコントロールをフォームにドッキングして作成します。  
  
 コントロールをドッキングするときは、どちらの親コンテナーの端にコントロールを固定するかを決定します。  <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定した場合、コントロールの右端が親コントロールの右端にドッキングされます。  さらに、コントロールがドッキングされた端は、そのコンテナー コントロールに合うようにサイズ変更されます。  <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティの機能の詳細については、「[方法 : Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)」を参照してください。  
  
 この手順は、機能を追加してアプリケーションを Microsoft Outlook のようにするのではなく、フォーム上に <xref:System.Windows.Forms.SplitContainer> などのコントロールを配置します。  
  
 このユーザー インターフェイスを作成するには、左側のパネルに <xref:System.Windows.Forms.TreeView> コントロールを含む <xref:System.Windows.Forms.SplitContainer> コントロール内に、すべてのコントロールを配置します。  <xref:System.Windows.Forms.SplitContainer> コントロールの右側のパネルには、第 2 の <xref:System.Windows.Forms.SplitContainer> コントロールが含まれます。第 2 のコントロールでは、上部に <xref:System.Windows.Forms.ListView> コントロール、その下部に <xref:System.Windows.Forms.RichTextBox> コントロールが配置されます。  これらの <xref:System.Windows.Forms.SplitContainer> コントロールを使用すると、フォーム上の他のコントロールを個別にサイズ変更できます。  この手順に示される手法を応用して、独自のカスタム ユーザー インターフェイスを作成できます。  
  
### プログラムで Outlook スタイルのユーザー インターフェイスを作成するには  
  
1.  フォーム内で、ユーザー インターフェイスを構成する各コントロールを宣言します。  この例では、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.SplitContainer>、および <xref:System.Windows.Forms.RichTextBox> の各コントロールを使用して、Microsoft Outlook のユーザー インターフェイスを模倣します。  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
  
    ```  
  
2.  ユーザー インターフェイスを定義するプロシージャを作成します。  次のコードは、フォームが Microsoft Outlook のユーザー インターフェイスに似た外観になるように、プロパティを設定しています。  ただし、他のコントロールを使用したり、異なる方法でコントロールをドッキングしたりすることによって、同じように柔軟性を持つ他のユーザー インターフェイスも簡単に作成できます。  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
  
    ```  
  
3.  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では、`New()` プロシージャで作成したプロシージャの呼び出しを追加します。  [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] では、フォーム クラスのコンストラクターに次のコード行を追加します。  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)   
 [方法 : デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)