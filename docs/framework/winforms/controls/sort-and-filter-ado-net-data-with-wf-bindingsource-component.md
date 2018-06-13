---
title: '方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: 3b58c4f3a53156ab01fb0c0c46b9a9b8d3fea84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538072"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する
並べ替えやフィルタ リングの機能を公開することができます<xref:System.Windows.Forms.BindingSource>を介して制御、<xref:System.Windows.Forms.BindingSource.Sort%2A>と<xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティです。 基になるデータ ソースが場合は、単純な並べ替えを適用することができます、 <xref:System.ComponentModel.IBindingList>、フィルターを適用し、高度なデータ ソースがときの並べ替えと、<xref:System.ComponentModel.IBindingListView>です。 <xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティには標準[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]構文: データ ソースのデータの列の名前を表す文字列が続く`ASC`または`DESC`一覧を昇順または降順で並べ替える必要があるかどうかを示すためにします。 高度な並べ替えまたは各列をコンマ区切り記号で区切って複数列の並べ替えを設定することができます。 <xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティには文字列式を指定します。  
  
> [!NOTE]
>  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
### <a name="to-filter-data-with-the-bindingsource"></a>BindingSource でデータをフィルター処理  
  
-   設定、<xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティを使用する式。  
  
     次のコード例では、式は、列名の後に、列に必要な値です。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>BindingSource でデータを並べ替える  
  
1.  設定、<xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティを続けて使用する列名`ASC`または`DESC`昇順または降順を示すためにします。  
  
2.  複数の列をコンマで区切ります。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>例  
 次のコード例に、Northwind サンプル データベースの Customers テーブルからデータを読み込む、<xref:System.Windows.Forms.DataGridView>制御、およびフィルターし、表示されるデータを並べ替えます。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例を実行するコードを貼り付けます、フォームが含まれていますが、<xref:System.Windows.Forms.BindingSource>という名前`BindingSource1`と<xref:System.Windows.Forms.DataGridView>という`dataGridView1`です。 処理、 <xref:System.Windows.Forms.Form.Load> 、フォームの呼び出しのイベント`InitializeSortedFilteredBindingSource`load イベント ハンドラー メソッドにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [方法 : サンプル データベースをインストールする](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)
