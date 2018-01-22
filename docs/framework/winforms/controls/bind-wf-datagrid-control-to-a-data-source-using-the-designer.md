---
title: "方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする"
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
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3913ffe046bb55e31d8be223061af61371a47418
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォーム<xref:System.Windows.Forms.DataGrid>コントロールは具体的には、データ ソースから情報を表示するように設計されています。 デザイン時に設定して、コントロールをバインドする、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ、または呼び出すことによって実行時に、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドです。 さまざまなデータ ソースからデータを表示できますが、最も一般的なソース、データセットとデータのビューです。  
  
 デザイン時に、データ ソースが利用可能な場合は — たとえば、フォームには、データセットまたはデータ ビューのインスタンスが含まれている場合: デザイン時に、データ ソースにグリッドをバインドすることができます。 グリッドで、データのようをプレビューできます。  
  
 実行時にプログラムでは、グリッドをバインドすることもできます。 これは、実行時に取得した情報に基づいてデータ ソースを設定する場合に便利です。 たとえば、アプリケーションは、ユーザーに表示するテーブルの名前を指定を使用できます可能性があります。 データ ソースがデザイン時に存在しない状況で必要です。 これには、配列、コレクション、型指定されていないデータセット、およびデータ リーダーなどのデータ ソースが含まれます。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGrid>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>コントロールに含まれていない、**ツールボックス**既定です。 追加の詳細については、次を参照してください。[する方法: ツールボックス アイテムの追加](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)です。 また、 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、使用することができます、**データ ソース**デザイン時のデータ バインディングのウィンドウ。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>デザイナーで 1 つのテーブルにデータ グリッド コントロールにデータ バインドする  
  
1.  コントロールの設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティにバインドするデータ項目を含むオブジェクトをします。  
  
2.  データ ソースがデータセットの場合は、設定、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティにバインドするテーブルの名前にします。  
  
3.  データ ソースが、データセットまたはデータセットのテーブルに基づいたデータ ビューの場合は、データセットへのデータ、フォームにコードを追加します。  
  
     実際に使用するコードは、データセットがデータを取得する場所によって異なります。 データセットは、データベースから直接登録されているが、通常を呼び出した場合、`Fill`という名前のデータセットに読み込まれる次のコード例のように、データ アダプターの`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (省略可能)グリッドに適切なテーブルのスタイルおよび列のスタイルを追加します。  
  
     テーブルのスタイルがない場合、テーブルが表示されますが、最低限の書式とすべての列が表示されます。  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>デザイナーでデータセットの複数のテーブルにデータ グリッド コントロールにデータ バインドする  
  
1.  コントロールの設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>プロパティにバインドするデータ項目を含むオブジェクトをします。  
  
2.  (つまり、relation オブジェクトが含まれている) 場合、データセットに関連するテーブルが含まれる場合、設定、<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティを親テーブルの名前にします。  
  
3.  データセットを読み込むコードを記述します。  
  
## <a name="see-also"></a>参照  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows フォームでのデータ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Visual Studio でのデータへのアクセス](/visualstudio/data-tools/accessing-data-in-visual-studio)
