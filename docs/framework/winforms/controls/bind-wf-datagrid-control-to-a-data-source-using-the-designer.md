---
title: "方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする | Microsoft Docs"
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
  - "バインド コントロール"
  - "バインド コントロール, DataGrid コントロール"
  - "データ バインド, DataGrid コントロール"
  - "データ バインド コントロール, DataGrid"
  - "DataGrid コントロール [Windows フォーム], データ バインド"
  - "データセット [Windows フォーム], バインド (DataGrid コントロールに)"
  - "Windows フォーム コントロール, データ バインド"
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームの <xref:System.Windows.Forms.DataGrid> コントロールは、データ ソースの情報を表示するようにデザインされています。  このコントロールは、<xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティおよび <xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティを設定してデザイン時にバインドするか、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを呼び出して実行時にバインドします。  各種データ ソースのデータを表示できますが、最も一般的なソースはデータセットとデータ ビューです。  
  
 デザイン時にデータ ソースを利用できる場合、たとえばフォームにデータセットやデータ ビューのインスタンスが含まれる場合などは、デザイン時にグリッドをデータ ソースにバインドできます。  その場合は、データがグリッド上でどのように見えるかをプレビューできます。  
  
 実行時にプログラムでグリッドを連結することもできます。  この方法は、実行時に取得した情報に基いてデータ ソースを設定する必要があるときに便利です。  たとえば、表示するテーブルの名前をユーザーが指定できるアプリケーションなどの場合です。  実行時の連結は、データ ソースがデザイン時に存在しない場合にも必要です。  この場合のデータ ソースとしては、配列、コレクション、型指定されていないデータセット、データ リーダーなどが挙げられます。  
  
 次の手順では、<xref:System.Windows.Forms.DataGrid> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] では、既定で <xref:System.Windows.Forms.DataGrid> コントロールは**ツールボックス**に含まれていません。  コントロールの追加の詳細については、「[How to: Add Items to the Toolbox](http://msdn.microsoft.com/ja-jp/458e119e-17fe-450b-b889-e31c128bd7e0)」を参照してください。  また、[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] では、**\[データ ソース\]** ウィンドウを使ってデザイン時のデータ バインディングを設定します。  詳細については、「[Visual Studio でのデータへのコントロールのバインド](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーで DataGrid コントロールを単一のテーブルのデータにバインドするには  
  
1.  コントロールの <xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティに、連結するデータ項目を含むオブジェクトを設定します。  
  
2.  データ ソースがデータセットである場合は、<xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティに連結するテーブルの名前を設定します。  
  
3.  データ ソースが、データセット テーブルに基づくデータセットまたはデー タビューの場合は、そのデータセットにデータを読み込むためのコードをフォームに追加します。  
  
     実際に使用するコードは、データセットがデータをどこで取得するかに依存します。  データセットにデータベースのデータを直接読み込む場合は、通常はデータ アダプターの `Fill` メソッドを呼び出します。次のコード例では、`DsCategories1` というデータセットにデータを読み込んでいます。  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  \(必要に応じて\) 適切なテーブル スタイルと列スタイルをグリッドに追加します。  
  
     テーブル スタイルがなくてもテーブルを表示できますが、その場合は最低限の書式だけが適用され、すべての列が表示されます。  
  
### デザイナーで DataGrid コントロールをデータセットの複数のテーブルにデータ連結するには  
  
1.  コントロールの <xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティに、連結するデータ項目を含むオブジェクトを設定します。  
  
2.  データセットに関連テーブルが含まれる場合 \(つまり、リレーションシップ オブジェクトが含まれる場合\)、<xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティに親テーブルの名前を設定します。  
  
3.  データセットにデータを読み込むコードを記述します。  
  
## 参照  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Windows フォームでのデータ バインド](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Visual Studio でのデータへのアクセス](../Topic/Accessing%20data%20in%20Visual%20Studio.md)