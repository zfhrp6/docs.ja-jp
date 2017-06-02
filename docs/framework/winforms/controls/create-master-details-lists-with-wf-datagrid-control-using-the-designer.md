---
title: "方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する | Microsoft Docs"
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
  - "DataGrid コントロール [Windows フォーム], マスター/詳細リスト"
  - "マスター/詳細リスト"
  - "関連テーブル, 表示 (DataGrid コントロールで)"
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Data.DataSet> に一連の互いに関連するテーブルが含まれている場合は、2 つの <xref:System.Windows.Forms.DataGrid> コントロールを使用してデータをマスター\/詳細形式で表示できます。  一方の <xref:System.Windows.Forms.DataGrid> をマスター グリッドに指定し、もう一方を詳細グリッドに指定します。  マスター リストのエントリを選択すると、関連するすべての子エントリが詳細リストに表示されます。  たとえば、<xref:System.Data.DataSet> に Customers テーブルおよび関連する Orders テーブルが含まれている場合は、Customers テーブルをマスター グリッドに指定し、Orders テーブルを詳細グリッドに指定します。  マスター グリッドから顧客が選択されると、Orders テーブル内でその顧客に関連するすべての注文が、詳細グリッドに表示されます。  
  
 次の手順には、**Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーでマスター\/詳細リストを作成するには  
  
1.  フォームに 2 つの <xref:System.Windows.Forms.DataGrid> コントロールを追加します。  詳細については、「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] では、既定で <xref:System.Windows.Forms.DataGrid> コントロールは**ツールボックス**に含まれていません。  詳細については、「[How to: Add Items to the Toolbox](http://msdn.microsoft.com/ja-jp/458e119e-17fe-450b-b889-e31c128bd7e0)」を参照してください。  
  
    > [!NOTE]
    >  以下の手順は、[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] には当てはまりません。[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] では、**\[データ ソース\]** ウィンドウを使ってデザイン時のデータ バインディングを設定します。  詳細については、「[Visual Studio でのデータへのコントロールのバインド](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)」および「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)」を参照してください。  
  
2.  **サーバー エクスプローラー**から 2 つ以上のテーブルをフォームにドラッグします。  
  
3.  **\[データ\]** メニューの **\[データセットの生成\]** をクリックします。  
  
4.  XML デザイナーを使用して、テーブル間にリレーションシップを設定します。  詳細については、MSDN の「方法 : XML スキーマとデータセットに一対多リレーションシップを作成する」を参照してください。  
  
5.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、リレーションシップを保存します。  
  
6.  マスター グリッドに指定する <xref:System.Windows.Forms.DataGrid> コントロールを以下のように設定します。  
  
    1.  <xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティのドロップダウン リストで <xref:System.Data.DataSet> を選択します。  
  
    2.  <xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティのドロップダウン リストでマスター テーブル \(たとえば、"Customers"\) を選択します。  
  
7.  詳細グリッドに指定する <xref:System.Windows.Forms.DataGrid> コントロールを以下のように設定します。  
  
    1.  <xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティのドロップダウン リストで <xref:System.Data.DataSet> を選択します。  
  
    2.  <xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティのドロップダウン リストでマスター テーブルと詳細テーブルの間のリレーションシップ \(たとえば、"Customers.CustOrd"\) を選択します。  リレーションシップを表示するには、ドロップダウン リストのマスター テーブルの横にあるプラス \(**\+**\) 記号をクリックして、ノードを展開します。  
  
## 参照  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [Visual Studio でのデータへのコントロールのバインド](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)