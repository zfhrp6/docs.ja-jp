---
title: "DataGridView コントロールのアーキテクチャ (Windows フォーム) | Microsoft Docs"
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
  - "DataGridView コントロール [Windows フォーム], アーキテクチャ"
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# DataGridView コントロールのアーキテクチャ (Windows フォーム)
<xref:System.Windows.Forms.DataGridView> コントロールとその関連クラスは、表形式のデータを表示および編集するための柔軟で拡張可能なシステムとして設計されています。  これらのクラスはすべて <xref:System.Windows.Forms?displayProperty=fullName> 名前空間に含まれており、どのクラス名にも "DataGridView" というプリフィックスが付いています。  
  
## アーキテクチャの要素  
 <xref:System.Windows.Forms.DataGridView> の主要なコンパニオン クラスは <xref:System.Windows.Forms.DataGridViewElement> から派生しています。  次のオブジェクト モデルは、<xref:System.Windows.Forms.DataGridViewElement> 継承階層構造を示しています。  
  
 ![DataGridViewElement オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewelement.png "DataGridViewElement")  
DataGridViewElement オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewElement> クラスは親となる <xref:System.Windows.Forms.DataGridView> コントロールへの参照を提供し、<xref:System.Windows.Forms.DataGridViewElement.State%2A> プロパティを備えています。このプロパティは、<xref:System.Windows.Forms.DataGridViewElementStates> 列挙体の値の組み合わせを表す値を取ります。  
  
 以下のセクションでは、<xref:System.Windows.Forms.DataGridView> のコンパニオン クラスについて詳しく説明します。  
  
### DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> 列挙体には次の値が含まれます。  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates>  
  
 この列挙体の値はビット単位の論理演算子と組み合わせて使用できるため、<xref:System.Windows.Forms.DataGridViewElement.State%2A> プロパティで一度に複数の状態を表現できます。  たとえば、<xref:System.Windows.Forms.DataGridViewElement> を <xref:System.Windows.Forms.DataGridViewElementStates> かつ <xref:System.Windows.Forms.DataGridViewElementStates> かつ <xref:System.Windows.Forms.DataGridViewElementStates> の状態にすることができます。  
  
### セルとバンド  
 <xref:System.Windows.Forms.DataGridView> コントロールは、セルとバンドという 2 種類の基本オブジェクトから構成されています。  すべてのセルは <xref:System.Windows.Forms.DataGridViewCell> 基本クラスから派生しています。  バンドには <xref:System.Windows.Forms.DataGridViewColumn> と <xref:System.Windows.Forms.DataGridViewRow> の 2 種類があり、どちらも <xref:System.Windows.Forms.DataGridViewBand> 基本クラスから派生しています。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールはさまざまなクラスとやり取りを行いますが、最もよく使用されるのは <xref:System.Windows.Forms.DataGridViewCell>、<xref:System.Windows.Forms.DataGridViewColumn>、<xref:System.Windows.Forms.DataGridViewRow> です。  
  
### DataGridViewCell  
 セルは <xref:System.Windows.Forms.DataGridView> で行われるやり取りの基本単位です。  表示はセルを中心として行われますし、多くの場合、データ入力はセルを通じて実行されます。  セルにアクセスするには、<xref:System.Windows.Forms.DataGridViewRow> クラスの <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> コレクションを使用します。選択中のセルにアクセスするには、<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> コレクションを使用します。  次のオブジェクト モデルは、この使用方法と <xref:System.Windows.Forms.DataGridViewCell> 継承階層構造を示しています。  
  
 ![DataGridViewCell オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewcell.png "DataGridViewCell")  
DataGridViewCell オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewCell> 型は、すべてのセル型の派生元となる抽象基本クラスです。  <xref:System.Windows.Forms.DataGridViewCell> とその派生型は Windows フォーム コントロールではありませんが、その中のいくつかは Windows フォーム コントロールをホストします。  セルで使用できる編集機能は、通常は、ホストされるコントロールによって処理されます。  
  
 <xref:System.Windows.Forms.DataGridViewCell> オブジェクトの外観と描画機能は、Windows フォーム コントロールとは異なる方法で制御されています。  <xref:System.Windows.Forms.DataGridViewCell> オブジェクトの外観を制御しているのは <xref:System.Windows.Forms.DataGridView> です。  <xref:System.Windows.Forms.DataGridView> コントロールのプロパティとイベントを操作することで、セルの外観と動作を大幅にカスタマイズです。  <xref:System.Windows.Forms.DataGridView> コントロールの機能を越える特殊なカスタマイズを行うときは、<xref:System.Windows.Forms.DataGridViewCell> またはその子クラスから派生した独自のクラスを実装します。  
  
 <xref:System.Windows.Forms.DataGridViewCell> から派生しているクラスを次に示します。  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   カスタムのセル型  
  
### DataGridViewColumn  
 <xref:System.Windows.Forms.DataGridView> コントロールに関連付けられているデータ ストアのスキーマは、<xref:System.Windows.Forms.DataGridView> コントロールの列で表現されます。  <xref:System.Windows.Forms.DataGridView> コントロールの列にアクセスするには、<xref:System.Windows.Forms.DataGridView.Columns%2A> コレクションを使用します。  選択中の列にアクセスするには、<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> コレクションを使用します。  次のオブジェクト モデルは、この使用方法と <xref:System.Windows.Forms.DataGridViewColumn> 継承階層構造を示しています。  
  
 ![DataGridViewColumn オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.png "DataGridViewColumn")  
DataGridViewColumn オブジェクト モデル  
  
 いくつかの重要なセル型には、対応する列型があります。  これらの型は <xref:System.Windows.Forms.DataGridViewColumn> 基本クラスから派生しています。  
  
 <xref:System.Windows.Forms.DataGridViewColumn> から派生しているクラスを次に示します。  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   カスタムの列型  
  
### DataGridView 編集コントロール  
 高度な編集機能をサポートしているセルは、通常は、Windows フォーム コントロールから派生したホストされるコントロールを使用しています。  これらのコントロールは <xref:System.Windows.Forms.IDataGridViewEditingControl> インターフェイスも実装しています。  次のオブジェクト モデルは、これらのコントロールの使用方法を示しています。  
  
 ![DataGridView 編集コントロール オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewediting.png "DataGridViewEditing")  
DataGridView 編集コントロール オブジェクト モデル  
  
 次の編集コントロールは <xref:System.Windows.Forms.DataGridView> コントロールによって提供されます。  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 独自の編集コントロールを作成する方法については、「[方法 : Windows フォーム DataGridView Cells でコントロールをホストする](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)」を参照してください。  
  
 次の表は、セル型、列型、編集コントロールの関係を示しています。  
  
|セル型|ホストされるコントロール|列型|  
|---------|------------------|--------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|適用なし|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|適用なし|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|適用なし|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|適用なし|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> クラスは、<xref:System.Windows.Forms.DataGridView> コントロールのバインド先のデータ ストアに含まれているレコードのデータ フィールドを表示します。  <xref:System.Windows.Forms.DataGridView> コントロールの行にアクセスするには、<xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションを使用します。  選択中の行にアクセスするには、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A> コレクションを使用します。  次のオブジェクト モデルは、この使用方法と <xref:System.Windows.Forms.DataGridViewRow> 継承階層構造を示しています。  
  
 ![DataGridViewRow オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewrow.png "DataGridViewRow")  
DataGridViewRow オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewRow> から独自の型を派生させることもできますが、通常はその必要はありません。  <xref:System.Windows.Forms.DataGridView> コントロールには、<xref:System.Windows.Forms.DataGridViewRow> オブジェクトの動作をカスタマイズするための行関連のイベントとプロパティが数多く用意されています。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティを有効にすると、新しい行を追加するための特殊な行が最終行として表示されます。  この行は <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションの一部ですが、特殊な機能を備えているので注意が必要です。  詳細については、「[Windows フォーム DataGridView コントロールにおける新規レコード行の使用](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールにおける新規レコード行の使用](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)