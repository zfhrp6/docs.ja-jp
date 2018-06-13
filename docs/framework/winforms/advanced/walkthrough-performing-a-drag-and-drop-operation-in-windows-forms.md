---
title: 'チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 6c78a06e37de491e95d56d29c9d2f3e60b88e8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529459"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行
Windows ベースのアプリケーション内でドラッグ アンド ドロップ操作を実行する必要がありますを処理する、一連のイベント、特に、 <xref:System.Windows.Forms.Control.DragEnter>、 <xref:System.Windows.Forms.Control.DragLeave>、および<xref:System.Windows.Forms.Control.DragDrop>イベント。 情報の操作、使用可能なイベントのこれらのイベントの引数、ドラッグ アンド ドロップ操作を簡単に実現できます。  
  
## <a name="dragging-data"></a>データのドラッグ  
 すべてのドラッグ アンド ドロップ操作では、ドラッグから始まります。 ドラッグの開始時に収集するデータを有効にする機能は実装、<xref:System.Windows.Forms.Control.DoDragDrop%2A>メソッドです。  
  
 次の例で、<xref:System.Windows.Forms.Control.MouseDown>イベントが最も簡単なになっているために、ドラッグ操作を開始するため (ドラッグ アンド ドロップ操作のほとんどは、マウス ボタンが押されているで始まります)。 ただし、ドラッグ アンド ドロップ手順を開始するすべてのイベントを使用できることに注意してください。  
  
> [!NOTE]
>  特定のコントロールでは、ドラッグに固有のカスタム イベントがあります。 <xref:System.Windows.Forms.ListView>と<xref:System.Windows.Forms.TreeView>コントロール、たとえば、ある、<xref:System.Windows.Forms.TreeView.ItemDrag>イベント。  
  
#### <a name="to-start-a-drag-operation"></a>ドラッグ操作を開始するには  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> 、ドラッグを開始する場所を使用するコントロールのイベントを`DoDragDrop`ドラッグされるデータを設定するメソッドとドラッグ許可の結果が設定されます。 詳細については、<xref:System.Windows.Forms.DragEventArgs.Data%2A> および <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> を参照してください。  
  
     次の例では、ドラッグ操作を開始する方法を示します。 コントロールのドラッグが開始されるは、<xref:System.Windows.Forms.Button>コントロール、ドラッグされるデータは、文字列を表す、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、<xref:System.Windows.Forms.Button>制御、および許可された効果をコピーまたは移動します。  
  
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
    >  すべてのデータをパラメーターとして使用できます、`DoDragDrop`メソッド以外の場合は、上記の例では、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、 <xref:System.Windows.Forms.Button> (ではなく、値をハードコーディングまたはデータセットからデータを取得する) にコントロールが使用されたに関連するプロパティがあるため、ドラッグされている場所 (、<xref:System.Windows.Forms.Button>コントロール)。 ドラッグ アンド ドロップ操作を Windows ベースのアプリケーションに組み込む場合に、この点に留意してください。  
  
 ドラッグ操作が有効な状態を処理できます、 <xref:System.Windows.Forms.Control.QueryContinueDrag> 「アクセス許可を要求する」イベントのドラッグ操作を続行するシステムです。 このメソッドを処理する場合も、適切なポイントを展開するなど、ドラッグ操作に影響があるメソッドを呼び出すには<xref:System.Windows.Forms.TreeNode>で、<xref:System.Windows.Forms.TreeView>上にカーソルを合わせるとを制御します。  
  
## <a name="dropping-data"></a>データを削除します。  
 データの場所から Windows フォームまたはコントロールのドラッグを開始した後は必然的にする任意の場所にドロップします。 カーソルは、フォームまたはデータを削除するが正しく構成されているコントロールの領域を超えたときに変更されます。 設定して削除されたデータを受け入れるように Windows フォームまたはコントロール内の任意の領域ができる、<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティと処理、<xref:System.Windows.Forms.Control.DragEnter>と<xref:System.Windows.Forms.Control.DragDrop>イベント。  
  
#### <a name="to-perform-a-drop"></a>Drop を実行するには  
  
1.  設定、<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティを true にします。  
  
2.  `DragEnter`ドラッグされるデータが適切な型を確実に削除が行われる、コントロールのイベントを (この場合、 <xref:System.Windows.Forms.Control.Text%2A>)。 コード内の値にドロップが発生したときに発生する効果を設定し、<xref:System.Windows.Forms.DragDropEffects>列挙します。 詳細については、「<xref:System.Windows.Forms.DragEventArgs.Effect%2A>」を参照してください。  
  
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
    >  独自に定義することができます<xref:System.Windows.Forms.DataFormats>オブジェクトとして指定することによって、<xref:System.Object>のパラメーター、<xref:System.Windows.Forms.DataObject.SetData%2A>メソッドです。 必要があります、これには、実施する際に指定されたオブジェクトがシリアル化可能であります。 詳細については、「<xref:System.Runtime.Serialization.ISerializable>」を参照してください。  
  
3.  <xref:System.Windows.Forms.Control.DragDrop>を使用して、削除が行われる、コントロールのイベントを<xref:System.Windows.Forms.DataObject.GetData%2A>ドラッグされるデータを取得します。 詳細については、「<xref:System.Security.Cryptography.Xml.DataObject.Data%2A>」を参照してください。  
  
     次の例で、<xref:System.Windows.Forms.TextBox>コントロールは、(、削除が行われる) にドラッグされているコントロール。 コード セット、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>ドラッグされるデータと等しいを制御します。  
  
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
    >  さらに、使用できますが、<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>プロパティ、キーによって、ドラッグ アンド ドロップ操作中に押されているように、特定の効果の発生 (たとえば、これは、CTRL キーが押されたときに、ドラッグしたデータをコピーする標準的な)。  
  
## <a name="see-also"></a>関連項目  
 [方法: クリップボードにデータを追加する](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [方法: クリップボードからデータを取得する](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
