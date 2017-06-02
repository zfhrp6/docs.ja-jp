---
title: "方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する | Microsoft Docs"
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
  - "コントロール [Windows フォーム]、操作"
  - "BindingNavigator コントロール [Windows フォーム]、ボタンの追加"
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する
<xref:System.Windows.Forms.BindingNavigator> コントロールは、フォーム上のデータ バインド コントロールの移動や操作に用途が特化された <xref:System.Windows.Forms.ToolStrip> コントロールです。  
  
 <xref:System.Windows.Forms.BindingNavigator> コンポーネントは <xref:System.Windows.Forms.ToolStrip> コントロールであるため、簡単に変更でき、ユーザー向けの追加コマンドや代替コマンドを含めることができます。  
  
 次の手順では、<xref:System.Windows.Forms.TextBox> コントロールをデータにバインドし、フォームに追加した <xref:System.Windows.Forms.ToolStrip> コントロールを変更して、\[Load\]、\[Save\]、\[Cancel\] の各ボタンを追加します。  
  
### BindingNavigator コンポーネントに \[Load\] ボタン、\[Save\] ボタン、および \[Cancel\] ボタンを追加するには  
  
1.  フォームに <xref:System.Windows.Forms.TextBox> コントロールを追加します。  
  
2.  このコントロールを、データ ソースにバインドされている <xref:System.Windows.Forms.BindingSource> にバインドします。  この例では、<xref:System.Windows.Forms.BindingSource> はデータベースにバインドされています。  
  
3.  データセットとテーブル アダプターが生成されたら、<xref:System.Windows.Forms.BindingNavigator> コントロールをフォームにドラッグします。  
  
4.  <xref:System.Windows.Forms.BindingNavigator> コントロールの <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> プロパティを、コントロールにバインドされているフォーム上の <xref:System.Windows.Forms.BindingSource> に設定します。  
  
5.  <xref:System.Windows.Forms.BindingNavigator> コントロールを選択します。  
  
6.  スマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして **\[BindingNavigator タスク\]** ダイアログ ボックスを表示し、**\[項目の編集\]** をクリックします。  
  
     **項目コレクション エディター**が表示されます。  
  
7.  **項目コレクション エディター**で、次の手順を実行します。  
  
    1.  適切な型の <xref:System.Windows.Forms.ToolStripItem> を選択し、**\[追加\]** をクリックして、<xref:System.Windows.Forms.ToolStripSeparator> と 3 つの <xref:System.Windows.Forms.ToolStripButton> 項目を追加します。  
  
    2.  各ボタンの <xref:System.Windows.Forms.ToolStripItem.Name%2A> `` プロパティを、それぞれ `` LoadButton、SaveButton、CancelButton `` に設定します。  
  
    3.  各ボタンの <xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを、それぞれ `` Load、Save、Cancel `` に設定します。  
  
    4.  各ボタンの <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> プロパティを `` Text に設定します。  または、このプロパティを `` Image `` または `` ImageAndText `` に設定し、<xref:System.Windows.Forms.ToolStripItem.Image%2A> プロパティでイメージが表示されるように設定することもできます。  
  
    5.  **\[OK\]** をクリックしてダイアログ ボックスを閉じます。各ボタンが <xref:System.Windows.Forms.ToolStrip> に追加されます。  
  
8.  フォームを右クリックし、**\[コードの表示\]** をクリックします。  
  
9. コード エディターで、テーブル アダプターにデータを読み込むコード行を見つけます。  このコードは、手順 2. でデータ バインディングを設定したときに生成されます。  たとえば、`TableAdapterName.Fill(DataSetName.TableName)` のようになります。  このコードは、一般にフォームの <xref:System.Windows.Forms.Form.Load> イベントに含まれます。  
  
10. 作成済みの `` **\[Load\]** `` <xref:System.Windows.Forms.ToolStripButton> の <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成し、データ読み込みコードをこのハンドラーに移動します。  
  
     コードは次のようになります。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. 作成済みの **\[Save\]** `` <xref:System.Windows.Forms.ToolStripButton> の <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成し、コントロールがバインドされている、テーブル内のデータを更新するコードを記述します。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingNavigator> コンポーネントには、既に `` **\[Save\]** ボタンが設定されている場合もありますが、Windows フォーム デザイナーによってコードは生成されていません。  このような場合は、<xref:System.Windows.Forms.ToolStrip> で新しいボタンを作成するのではなく、既存のボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベント ハンドラーに前述のコードを配置できます。  ただし、ボタンは既定で無効になっているため、ボタンの <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> プロパティを `true` に設定し、ボタンが適切に機能するようにします。  
  
12. 作成済みの `` **\[Cancel\]** `` <xref:System.Windows.Forms.ToolStripButton> の <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成し、表示されているデータ レコードに対する変更をキャンセルするコードを記述します。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> メソッドのスコープはデータ行です。  個々のレコードの表示中に行った変更は、次のレコードに移動する前に保存してください。  
  
## 参照  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.ToolStrip>   
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [BindingSource コンポーネントの概要](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)