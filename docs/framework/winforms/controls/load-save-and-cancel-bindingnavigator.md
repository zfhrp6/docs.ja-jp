---
title: "方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する"
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
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4bc4f53c404e3767b9f98ca5ab46b19db31f9c6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する
<xref:System.Windows.Forms.BindingNavigator>コントロールは、特別な用途<xref:System.Windows.Forms.ToolStrip>コントロールを移動して、データにバインドされている、フォーム上のコントロールを操作対象とします。  
  
 なっているため、<xref:System.Windows.Forms.ToolStrip>コントロール、<xref:System.Windows.Forms.BindingNavigator>コンポーネントは、ユーザーの追加または代替のコマンドを含める簡単に変更できます。  
  
 次の手順で、<xref:System.Windows.Forms.TextBox>コントロールは、データにバインドされ、<xref:System.Windows.Forms.ToolStrip>をフォームに追加されたコントロールは、保存、負荷を含めるし、キャンセル ボタンに変更します。  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>負荷を追加するには、保存、およびキャンセル BindingNavigator コンポーネントへのボタン  
  
1.  フォームに <xref:System.Windows.Forms.TextBox> コントロールを追加します。  
  
2.  バインドする<xref:System.Windows.Forms.BindingSource>、これが、データ ソースにバインドします。 この例で、<xref:System.Windows.Forms.BindingSource>はデータベースにバインドします。  
  
3.  データセットとテーブルのアダプターが生成されると、ドラッグ、<xref:System.Windows.Forms.BindingNavigator>をフォームにコントロールできます。  
  
4.  設定、<xref:System.Windows.Forms.BindingNavigator>コントロールの<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>プロパティを<xref:System.Windows.Forms.BindingSource>コントロールにバインドされている形式にします。  
  
5.  <xref:System.Windows.Forms.BindingNavigator> コントロールを選択します。  
  
6.  スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ため、 **BindingNavigator タスク**ダイアログが表示され選択**アイテムの編集**.  
  
     **Items コレクション エディター**が表示されます。  
  
7.  **Items コレクション エディター**次を完了します。  
  
    1.  追加、 <xref:System.Windows.Forms.ToolStripSeparator> 3<xref:System.Windows.Forms.ToolStripButton>項目の種類の適切な選択を<xref:System.Windows.Forms.ToolStripItem> をクリックし、**追加**ボタンをクリックします。  
  
    2.  設定、<xref:System.Windows.Forms.ToolStripItem.Name%2A>ボタンのプロパティ**LoadButton**、**SaveButton**、および**CancelButton**、それぞれします。  
  
    3.  設定、<xref:System.Windows.Forms.ToolStripItem.Text%2A>ボタンのプロパティ**ロード**`,` **保存**、および**キャンセル**です。  
  
    4.  設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>するボタンの各プロパティ**テキスト**です。 このプロパティを設定する代わりに、**イメージ**または**ImageAndText**に表示されるイメージを設定し、<xref:System.Windows.Forms.ToolStripItem.Image%2A>プロパティです。  
  
    5.  をクリックして**OK**  ダイアログ ボックスを閉じます。ボタンに追加されて、<xref:System.Windows.Forms.ToolStrip>です。  
  
8.  フォームを右クリックして選択**コードの表示**です。  
  
9. コード エディターでは、テーブル アダプターにデータを読み込むコードの行を検索します。 このコードは、手順 2. でデータ バインディングを設定するときに生成されました。 コードを次のようにする必要があります:`TableAdapterName.Fill(DataSetName.TableName)`です。 ほとんどは、フォームのされる可能性が高い<xref:System.Windows.Forms.Form.Load>イベント。  
  
10. イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**ロード**<xref:System.Windows.Forms.ToolStripButton>以前に作成し、このデータの読み込みのコードを移動します。  
  
     コードは次のようになります。  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**保存**<xref:System.Windows.Forms.ToolStripButton>先ほど作成したし、テーブル コントロール内のデータを更新するコードの記述にバインドします。  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  場合によっては、<xref:System.Windows.Forms.BindingNavigator>コンポーネントが既に与えられて、**保存**ボタン、コードではなく、によって生成された Windows フォーム デザイナー。 上記のコードを配置するこの例では、<xref:System.Windows.Forms.ToolStripItem.Click>に完全に新しいボタンを作成するのではなく、そのボタンのイベント ハンドラー、<xref:System.Windows.Forms.ToolStrip>です。 ただし、ボタンは既定では無効ため、設定する必要があります、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>するボタンのプロパティ`true`に正しくボタン関数。  
  
12. イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**キャンセル**<xref:System.Windows.Forms.ToolStripButton>以前に作成し、表示されるデータのレコードへの変更をキャンセルするコードを記述します。  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>メソッドのスコープは、データの行にします。 次のレコードに移動する前に個々 のレコードの表示中に加えたあらゆる変更を保存します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [BindingSource コンポーネントの概要](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
