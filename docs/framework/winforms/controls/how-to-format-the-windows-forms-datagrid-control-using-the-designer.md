---
title: "方法 : デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b47b0c2353764f5452c2bb3f6ca37af11d6d904c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>方法 : デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 さまざまな部分をさまざまな色を適用する、<xref:System.Windows.Forms.DataGrid>コントロールのヘルプ情報に簡単にするための読み取りおよび解釈することができます。 色は、行と列に適用できます。 行と列も非表示にしたり各自の判断で示すようにします。  
  
 書式設定の 3 つの基本的な要素があります、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
-   データを表示する既定のスタイルを確立するためにプロパティを設定することができます。  
  
-   そのベースから、実行時に特定のテーブルの表示方法をカスタマイズできます。  
  
-   最後に、色と同様に、データ グリッドに表示される列を変更することができ、その他の書式を示します。  
  
 最初の手順として、データ グリッドを書式設定のプロパティを設定することができます、<xref:System.Windows.Forms.DataGrid>自体です。 これらの色と書式の選択元となることができますし、変更を加えたデータ テーブルと表示される列に応じて、ベースを形成します。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGrid>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>コントロールに含まれていない、**ツールボックス**既定です。 詳細については、次を参照してください。[する方法: ツールボックス アイテムの追加](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid コントロールの既定のスタイルを確立するために  
  
1.  <xref:System.Windows.Forms.DataGrid> コントロールを選択します。  
  
2.  **プロパティ**ウィンドウで、必要に応じて、次のプロパティを設定します。  
  
    |プロパティ|説明|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor`プロパティ グリッドの偶数行の色を定義します。 設定すると、<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>は異なる色に、その他のすべての行に設定されてこの新しい色 (1、3、5、およびなどの行数)。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|グリッドの偶数行の背景色 (0、2、4、6、およびなどの行数)。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|一方、<xref:System.Windows.Forms.DataGrid.BackColor%2A>と<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>プロパティ グリッドで、行の色を決定する、<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>プロパティは、下のグリッドをスクロールするときに、または、いくつかの行だけの場合にのみ表示行エリアの外、領域の色を決定します。グリッドに含まれています。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|いずれかのグリッドの罫線のスタイル、<xref:System.Windows.Forms.BorderStyle>列挙値。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|グリッドの上にすぐに表示されるグリッドのウィンドウ キャプションの背景色。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|グリッドの上部のキャプションのフォントです。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|グリッドのウィンドウ キャプションの背景色。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|グリッドでテキストを表示するために使用するフォントです。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|データ グリッドの行のデータが表示されるフォントの色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|データ グリッドのグリッド線の色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|いずれかと、グリッドのセルを区切る線のスタイル、<xref:System.Windows.Forms.DataGridLineStyle>列挙値。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|行および列ヘッダーの背景色です。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|列ヘッダーに使用するフォントです。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|列ヘッダーのテキストと正符号 (+) マイナス記号 (-) を展開し、複数の関連するテーブルと行を折りたたむグリフなど、グリッドの列ヘッダーの背景色が表示されます。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|子テーブル、リレーションシップ名となどへのリンクなど、データ グリッド内のすべてのリンクのテキストの色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|子テーブルでは、これは親の行の背景色です。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|子テーブルでは、これは親の行の前景色です。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|親行のテーブルと列の名前が表示されるかどうかを決定、<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列挙します。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|グリッドの列の既定の幅 (ピクセル単位)。 リセットする前に、このプロパティを設定、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ (いずれかとは別に、または、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド)、またはプロパティには影響はありません。<br /><br /> プロパティは、0 より小さい値に設定できません。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|グリッド内の行のピクセル単位で行の高さ。 リセットする前に、このプロパティを設定、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ (いずれかとは別に、または、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド)、またはプロパティには影響はありません。<br /><br /> プロパティは、0 より小さい値に設定できません。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|グリッドの行ヘッダーの幅。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|行またはセルを選択すると、これは、背景色。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|行またはセルを選択すると、これは、前景色です。|  
  
    > [!NOTE]
    >  コントロールの色をカスタマイズするとき、コントロールを不適切な色の選択 (たとえば、赤と緑) のためにアクセスすることができます。 使用できる色を使用して、**システム カラー**パレットをこの問題を回避します。  
  
     次の手順が必要です、<xref:System.Windows.Forms.DataGrid>コントロールをデータ テーブルにバインドします。 詳細については、次を参照してください。[する方法: Windows フォーム DataGrid コントロールをデータ ソースにバインド](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)です。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>デザイン時に、データ テーブルのテーブルと列のスタイルを設定するには  
  
1.  選択、<xref:System.Windows.Forms.DataGrid>フォーム上のコントロールです。  
  
2.  **プロパティ**ウィンドウで、<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティをクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンをクリックします。  
  
3.  **DataGridTableStyle コレクション エディター**ダイアログ ボックスで、をクリックして**追加**コレクションに、テーブルのスタイルを追加します。  
  
     **DataGridTableStyle コレクション エディター**マッピング テーブル スタイルの削除、表示の設定とレイアウト プロパティ、およびセット テーブル スタイルの名前を追加することができます。  
  
4.  設定、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>プロパティを各テーブルのスタイルのマッピングの名前にします。  
  
     マッピング名は、どのテーブルで使用するどのテーブル スタイルを指定に使用されます。  
  
5.  **DataGridTableStyle コレクション エディター**、select、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>プロパティの省略記号ボタンをクリックし、(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")).  
  
6.  **DataGridColumnStyle コレクション エディター**  ダイアログ ボックスで、作成したテーブルのスタイルを列のスタイルを追加します。  
  
     **DataGridColumnStyle コレクション エディター**書式指定文字列のデータ列、および追加し、列のスタイルを削除、表示およびレイアウトのプロパティを設定およびマッピングの名前を設定します。  
  
    > [!NOTE]
    >  書式指定文字列の詳細については、次を参照してください。[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [方法: Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
