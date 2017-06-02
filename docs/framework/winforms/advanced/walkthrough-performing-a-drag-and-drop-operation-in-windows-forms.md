---
title: "チュートリアル : Windows フォームにおけるドラッグ アンド ドロップ操作の実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ドラッグ アンド ドロップ, Windows フォーム"
  - "Windows フォーム, ドラッグ アンド ドロップ操作"
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# チュートリアル : Windows フォームにおけるドラッグ アンド ドロップ操作の実行
Windows ベースのアプリケーション内でドラッグ アンド ドロップ操作を実行するには、<xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave>、<xref:System.Windows.Forms.Control.DragDrop> などの一連のイベントを処理する必要があります。  これらのイベントのイベント引数で提供される情報を使用することにより、ドラッグ アンド ドロップ操作を簡単に実現できます。  
  
## データのドラッグ  
 すべてのドラッグ アンド ドロップ操作は、ドラッグから始まります。  ドラッグが開始されたときにデータを収集できるようにする機能は、<xref:System.Windows.Forms.Control.DoDragDrop%2A> メソッドに実装されています。  
  
 次の例では、最も直観的な <xref:System.Windows.Forms.Control.MouseDown> イベントを使用してドラッグ操作を開始しています。これは、ほとんどのドラッグ アンド ドロップ操作は、マウス ボタンが押されることによって開始されるためです。  ただし、ドラッグ アンド ドロップの手順は任意のイベントを使用して開始できます。  
  
> [!NOTE]
>  ドラッグに関するカスタム イベントのあるコントロールもあります。  たとえば、<xref:System.Windows.Forms.ListView> コントロールと <xref:System.Windows.Forms.TreeView> コントロールには、<xref:System.Windows.Forms.TreeView.ItemDrag> イベントがあります。  
  
#### ドラッグ操作を開始するには  
  
1.  ドラッグが  開始されるコントロールの <xref:System.Windows.Forms.Control.MouseDown> のイベントでドラッグされるデータを設定するに `DoDragDrop` のメソッドを使用して実行できる処理のドラッグがあります。  詳細については、「<xref:System.Windows.Forms.DragEventArgs.Data%2A>」および「<xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>」を参照してください。  
  
     ドラッグ操作を開始する方法の例を次に示します。  ドラッグが開始されるコントロールは <xref:System.Windows.Forms.Button> コントロール、ドラッグされるデータは、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティを表す文字列、実行できる処理はコピーまたは移動のいずれかです。  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
  
    ```  
  
    > [!NOTE]
    >  `DoDragDrop` メソッドでは、任意のデータをパラメーターとして使用できます。上の例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティがドラッグの開始位置 \(<xref:System.Windows.Forms.Button> コントロール\) に関連するため、値をハードコーディングしたり、データセットからデータを取得したりせずに、このプロパティを使用しています。  Windows ベースのアプリケーションにドラッグ アンド ドロップ操作を組み込む場合には、この点を考慮してください。  
  
 ドラッグ操作が行われている間、<xref:System.Windows.Forms.Control.QueryContinueDrag> イベントを処理できます。これは、ドラッグ操作を続けてよいかどうかシステムの "許可を得る" イベントです。  このメソッドを処理するときは、たとえば、カーソルが置かれたときに <xref:System.Windows.Forms.TreeView> コントロールの <xref:System.Windows.Forms.TreeNode> を展開するなど、ドラッグ操作に影響するメソッドを呼び出すのにも適しています。  
  
## データのドロップ  
 Windows フォームまたはコントロール上の場所からデータのドラッグを開始したら、それをどこかにドロップする必要があります。  データをドロップできるように正しく設定されているフォームまたはコントロールの領域をカーソルが横切ると、カーソルの形が変わります。  <xref:System.Windows.Forms.Control.AllowDrop%2A> プロパティを設定し、<xref:System.Windows.Forms.Control.DragEnter> イベントと <xref:System.Windows.Forms.Control.DragDrop> イベントを処理することにより、Windows フォームまたはコントロール内の任意の領域で、ドロップされたデータを受け入れることができます。  
  
#### ドロップを実行するには  
  
1.  <xref:System.Windows.Forms.Control.AllowDrop%2A> プロパティを true に設定します。  
  
2.  ドロップ先のコントロールの `DragEnter` イベントで、ドラッグされるデータが適切な型 \(この場合、<xref:System.Windows.Forms.Control.Text%2A>\) であることを確認します。  次に、コードでは、ドロップしたときの効果を <xref:System.Windows.Forms.DragDropEffects> 列挙定数の値に設定します。  詳細については、「<xref:System.Windows.Forms.DragEventArgs.Effect%2A>」を参照してください。  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.DataObject.SetData%2A> メソッドの <xref:System.Object> パラメーターとして独自のオブジェクトを指定することで、固有の <xref:System.Windows.Forms.DataFormats> を定義できます。  その場合は、指定するオブジェクトがシリアル化できるオブジェクトであることを確認してください。  詳細については、「[ISerializable インターフェイス](frlrfSystemRuntimeSerializationISerializableClassTopic)」を参照してください。  
  
3.  ドロップ先のコントロールの <xref:System.Windows.Forms.Control.DragDrop> イベントで、<xref:System.Windows.Forms.DataObject.GetData%2A> メソッドを使用して、ドラッグされるデータを取得します。  詳細については、「[DtaObject.Data プロパティ](frlrfSystemSecurityCryptographyXmlDataObjectClassDataTopic)」を参照してください。  
  
     次の例では、データがドロップされるドラッグ先のコントロールは <xref:System.Windows.Forms.TextBox> コントロールです。  コードでは、<xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティをドラッグされたデータと同じ内容に設定します。  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
  
    ```  
  
    > [!NOTE]
    >  さらに、<xref:System.Windows.Forms.DragEventArgs.KeyState%2A> プロパティを使用して、ドラッグ アンド ドロップ操作中に押されたキーに応じて特定の効果が得られるようにできます。たとえば一般的に、Ctrl キーを押しながらドラッグしたデータはコピーされます。  
  
## 参照  
 [方法 : クリップボードにデータを追加する](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)   
 [方法 : クリップボードからデータを取得する](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)   
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)