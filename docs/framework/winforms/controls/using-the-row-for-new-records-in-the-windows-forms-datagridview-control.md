---
title: "Windows フォーム DataGridView コントロールにおける新規レコード行の使用 | Microsoft Docs"
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
  - "DataGridView コントロール [Windows フォーム], 追加 (新規レコード行を)"
  - "DataGridView コントロール [Windows フォーム], データ エントリ"
  - "行, 新規レコード"
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Windows フォーム DataGridView コントロールにおける新規レコード行の使用
アプリケーションでデータを編集するために <xref:System.Windows.Forms.DataGridView> を使用するときは、多くの場合、新しいデータ行をデータ ストアに追加する機能をユーザーに提供します。  <xref:System.Windows.Forms.DataGridView> コントロールはこの機能をサポートし、追加される新しいレコード行は常に最後の行として表示されます。  この行のヘッダーには、アスタリスク \(\*\) の記号が表示されます。  以下のセクションでは、新規レコード行を有効にしてプログラミングするときの考慮事項について説明します。  
  
## 新規レコード行の表示  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティを使用して、新規レコード行を表示するかどうかを指定します。  このプロパティの既定値は `true` です。  
  
 データがバインドされている場合、コントロールの <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティとデータ ソースの <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=fullName> プロパティが共に `true` であると、新規レコード行が表示されます。  これらのプロパティのいずれかが `false` の場合、行は表示されません。  
  
## 新規レコード行への既定のデータの読み込み  
 ユーザーが新規レコード行を現在の行として選択すると、<xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベントを生成します。  
  
 このイベントは新しい <xref:System.Windows.Forms.DataGridViewRow> へのアクセスを可能にし、新しい行に既定のデータを読み込むことができるようにします。  詳細については、「[方法 : Windows フォーム DataGridView コントロールの新しい行に既定値を指定する](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)」を参照してください。  
  
## 行コレクション  
 新規レコード行は、<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションに含まれますが、次の 2 つの点で動作の仕方が異なります。  
  
-   新規レコード行は、プログラムによって <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションから削除できません。  削除しようとすると、<xref:System.InvalidOperationException> がスローされます。  また、新規レコード行は、ユーザーが削除することもできません。  <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=fullName> メソッドは、この行を <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションから削除しません。  
  
-   新規レコード行の後に行を追加できません。  そのように設定しようとすると、<xref:System.InvalidOperationException> が生成されます。  このため、新規レコード行は、常に <xref:System.Windows.Forms.DataGridView> コントロールの最後の行になります。  行を追加する、<xref:System.Windows.Forms.DataGridViewRowCollection> のメソッド \(<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、および<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>\) はすべて、新規レコード行が存在するときに挿入メソッドを内部的に呼び出します。  
  
## 新規レコード行のビジュアル カスタマイズ  
 新規レコード行は、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A> プロパティで指定された行に基づいて作成されます。  この行に指定されていないセル スタイルは、他のプロパティから継承されます。  セル スタイルの継承の詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 新規レコード行のセルに表示される初期値は、各セルの <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> プロパティから取得されます。  セルの種類が <xref:System.Windows.Forms.DataGridViewImageCell> の場合、このプロパティはプレースホルダー イメージを返します。  それ以外の場合は、`null` を返します。  このプロパティは、カスタム値を返すようにオーバーライドできます。  ただし、セルの初期値は、新規レコード行にフォーカスが入ったときに <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベント ハンドラーによって置き換えることができます。  
  
 この行のヘッダーの標準アイコン \(矢印またはアスタリスク\) は公開されません。  このアイコンをカスタマイズする場合は、カスタムの <xref:System.Windows.Forms.DataGridViewRowHeaderCell> クラスを作成する必要があります。  
  
 標準アイコンは、行ヘッダー セルで使用されている <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> プロパティを使用します。  標準アイコンは、表示領域が不十分な場合は描画されません。  
  
 行ヘッダー セルに文字列値が設定され、テキストとアイコンの両方を表示する十分な領域がない場合は、アイコンが最初に無効にされます。  
  
## 並べ替え  
 非バインド モードでは、ユーザーが <xref:System.Windows.Forms.DataGridView> のコンテンツを並べ替えた場合でも、新規レコードは常に <xref:System.Windows.Forms.DataGridView> の最後に追加されます。  行を正確な位置に並べ替えるには、再度並べ替えを適用する必要があります。この動作は、<xref:System.Windows.Forms.ListView> コントロールの動作に似ています。  
  
 データ バインド モードと仮想モードでは、並べ替えを適用したときの挿入動作は、データ モデルの実装によって異なります。  [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] では、行がすぐに正確な位置に並べ替えられます。  
  
## 新規レコード行に関するその他の注意  
 この行の <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> プロパティは、`false` に設定できません。  そのように設定しようとすると、<xref:System.InvalidOperationException> が生成されます。  
  
 新規レコード行は、常に未選択の状態で作成されます。  
  
## 仮想モード  
 仮想モードを実装する場合は、新規レコード行がデータ モデルで必要になる時点と、新規レコード行の追加をロールバックする時点を監視する必要があります。  この機能の正確な実装は、データ モデルの実装とそのトランザクション セマンティクス \(たとえば、コミット スコープがセル レベルか、行レベルかなど\) によって異なります。  詳細については、「[Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの新しい行に既定値を指定する](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)