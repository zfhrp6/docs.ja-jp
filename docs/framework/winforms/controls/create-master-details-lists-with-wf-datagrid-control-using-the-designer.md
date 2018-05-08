---
title: '方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 20a6f059efab5469879d3c3a45f4005020414316
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>方法 : デザイナーで Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 場合、<xref:System.Data.DataSet>は一連の関連テーブルの 2 つ使用できます<xref:System.Windows.Forms.DataGrid>マスター/詳細形式でデータを表示するコントロール。 1 つ<xref:System.Windows.Forms.DataGrid>マスター グリッドに指定し、詳細グリッドに、もう一方を指定します。 マスターの一覧にエントリを選択すると、詳細の一覧ですべての関連する子エントリのとおりです。 たとえば場合、 <xref:System.Data.DataSet> Customers テーブルと関連の Orders テーブルを含むマスター グリッドに Customers テーブルと Orders テーブルに、詳細グリッドを指定するとします。 マスター グリッドから、顧客がオンの場合、すべての注文を Orders テーブル内でその顧客に関連付けられているの詳細グリッドに表示されます。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクト。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>デザイナーでマスター/詳細リストを作成するには  
  
1.  2 つ追加<xref:System.Windows.Forms.DataGrid>フォームのコントロールです。 詳細については、次を参照してください。[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>コントロールに含まれていない、**ツールボックス**既定です。 詳細については、次を参照してください。[する方法: ツールボックス アイテムの追加](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)です。  
  
    > [!NOTE]
    >  次の手順には適用されない[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]が使用される、**データ ソース**デザイン時のデータ バインディングのウィンドウ。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)と[する方法: Windows フォーム アプリケーションで関連するデータを表示](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)です。  
  
2.  次の 2 つ以上のテーブルをドラッグして**サーバー エクスプ ローラー**をフォームにします。  
  
3.  **データ**メニューの **データセットの生成**です。  
  
4.  XML デザイナーを使用してテーブル間のリレーションシップを設定します。 詳細については、次を参照してください。"する方法: 一対多を作成する XML スキーマおよびデータセットでリレーションシップ"msdn です。  
  
5.  選択して、リレーションシップを保存**すべて保存**から、**ファイル**メニュー。  
  
6.  構成、<xref:System.Windows.Forms.DataGrid>マスター グリッドを次のように指定するコントロール。  
  
    1.  選択、<xref:System.Data.DataSet>のドロップ ダウン リストから、<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティです。  
  
    2.  ドロップダウン リストからマスター テーブル (たとえば、"Customers") を選択、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティです。  
  
7.  構成、<xref:System.Windows.Forms.DataGrid>詳細グリッドを次のように指定するコントロール。  
  
    1.  選択、<xref:System.Data.DataSet>のドロップ ダウン リストから、<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティです。  
  
    2.  ドロップダウン リストから、マスター/詳細テーブル間の関係 (たとえば、"Customers.CustOrd") を選択、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティです。 リレーションシップを表示するために、プラス記号をクリックすると、ノードを展開します (**+**) ドロップダウン リストのマスター テーブルの横にある記号。  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [方法: データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
