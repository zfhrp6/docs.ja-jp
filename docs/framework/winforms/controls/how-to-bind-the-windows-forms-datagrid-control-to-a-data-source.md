---
title: '方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 62f61eb2d294baf007b0b3f749f3cf6b7f4857c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530303"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォーム<xref:System.Windows.Forms.DataGrid>コントロールは具体的には、データ ソースから情報を表示するように設計されています。 実行時に呼び出すことによって、コントロールをバインドする、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドです。 さまざまなデータ ソースからデータを表示できますが、最も一般的なソース、データセットとデータのビューです。  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>DataGrid コントロールをプログラムでデータ バインドする  
  
1.  データセットを読み込むコードを記述します。  
  
     データ ソースが、データセットまたはデータセットのテーブルに基づいたデータ ビューの場合は、データセットへのデータ、フォームにコードを追加します。  
  
     実際に使用するコードは、データセットがデータを取得する場所によって異なります。 データセットは、データベースから直接登録されているが、通常を呼び出した場合、`Fill`という名前のデータセットに読み込まれる次の例のように、データ アダプターの`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     場合は、データセットは、XML Web サービスから指定されている、通常、コードでサービスのインスタンスを作成し、データセットを返すメソッドのいずれかを呼び出します。 XML Web サービスからのデータセットをマージするには、ローカルのデータセットにします。 次の例と呼ばれる XML Web サービスのインスタンスを作成する方法を示しています`CategoriesService`を呼び出してその`GetCategories`メソッド、およびローカルのデータセットに結果のデータセットと呼ばれるマージ`DsCategories1`:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2.  呼び出す、<xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド、データ ソースとデータ メンバーを渡します。 データ メンバーを明示的に渡す必要がない場合は、空の文字列を渡します。  
  
    > [!NOTE]
    >  最初に、グリッドをバインドする場合は、コントロールを設定することができます<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティです。 ただし、これらを設定したら、これらのプロパティをリセットできません。 そのため、お勧め必ず使用すること、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドです。  
  
     次の例は、プログラムによってという名前のデータセット内の Customers テーブルにバインドする方法を示しています`DsCustomers1`:。  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Customers テーブルがデータセット内の唯一のテーブルの場合は、でしたまたはグリッドを連結するこの方法。  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  (省略可能)グリッドに適切なテーブルのスタイルおよび列のスタイルを追加します。 テーブルのスタイルがない場合、テーブルが表示されますが、最低限の書式とすべての列が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows フォームでのデータ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)
