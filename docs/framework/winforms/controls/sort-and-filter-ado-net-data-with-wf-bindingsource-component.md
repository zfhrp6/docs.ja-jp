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
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="7686b-102">方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する</span><span class="sxs-lookup"><span data-stu-id="7686b-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="7686b-103">並べ替えやフィルタ リングの機能を公開することができます<xref:System.Windows.Forms.BindingSource>を介して制御、<xref:System.Windows.Forms.BindingSource.Sort%2A>と<xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7686b-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="7686b-104">基になるデータ ソースが場合は、単純な並べ替えを適用することができます、 <xref:System.ComponentModel.IBindingList>、フィルターを適用し、高度なデータ ソースがときの並べ替えと、<xref:System.ComponentModel.IBindingListView>です。</span><span class="sxs-lookup"><span data-stu-id="7686b-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="7686b-105"><xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティには標準[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]構文: データ ソースのデータの列の名前を表す文字列が続く`ASC`または`DESC`一覧を昇順または降順で並べ替える必要があるかどうかを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="7686b-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="7686b-106">高度な並べ替えまたは各列をコンマ区切り記号で区切って複数列の並べ替えを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="7686b-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="7686b-107"><xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティには文字列式を指定します。</span><span class="sxs-lookup"><span data-stu-id="7686b-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7686b-108">接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="7686b-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="7686b-109">データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="7686b-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="7686b-110">詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7686b-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="7686b-111">BindingSource でデータをフィルター処理</span><span class="sxs-lookup"><span data-stu-id="7686b-111">To filter data with the BindingSource</span></span>  
  
-   <span data-ttu-id="7686b-112">設定、<xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティを使用する式。</span><span class="sxs-lookup"><span data-stu-id="7686b-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="7686b-113">次のコード例では、式は、列名の後に、列に必要な値です。</span><span class="sxs-lookup"><span data-stu-id="7686b-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="7686b-114">BindingSource でデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="7686b-114">To sort data with the BindingSource</span></span>  
  
1.  <span data-ttu-id="7686b-115">設定、<xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティを続けて使用する列名`ASC`または`DESC`昇順または降順を示すためにします。</span><span class="sxs-lookup"><span data-stu-id="7686b-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2.  <span data-ttu-id="7686b-116">複数の列をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="7686b-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="7686b-117">例</span><span class="sxs-lookup"><span data-stu-id="7686b-117">Example</span></span>  
 <span data-ttu-id="7686b-118">次のコード例に、Northwind サンプル データベースの Customers テーブルからデータを読み込む、<xref:System.Windows.Forms.DataGridView>制御、およびフィルターし、表示されるデータを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="7686b-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7686b-119">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7686b-119">Compiling the Code</span></span>  
 <span data-ttu-id="7686b-120">この例を実行するコードを貼り付けます、フォームが含まれていますが、<xref:System.Windows.Forms.BindingSource>という名前`BindingSource1`と<xref:System.Windows.Forms.DataGridView>という`dataGridView1`です。</span><span class="sxs-lookup"><span data-stu-id="7686b-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="7686b-121">処理、 <xref:System.Windows.Forms.Form.Load> 、フォームの呼び出しのイベント`InitializeSortedFilteredBindingSource`load イベント ハンドラー メソッドにします。</span><span class="sxs-lookup"><span data-stu-id="7686b-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7686b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7686b-122">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [<span data-ttu-id="7686b-123">方法 : サンプル データベースをインストールする</span><span class="sxs-lookup"><span data-stu-id="7686b-123">How to: Install Sample Databases</span></span>](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [<span data-ttu-id="7686b-124">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7686b-124">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
