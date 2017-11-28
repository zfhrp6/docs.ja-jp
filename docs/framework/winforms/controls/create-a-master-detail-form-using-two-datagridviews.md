---
title: "方法: Windows フォーム DataGridView コントロールの 2 つを使用してマスター/詳細フォームを作成します。"
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
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b18e26ff20496248e4525bc31722cf6fcbbc3da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="10110-102">方法 : Windows フォームの 2 つの DataGridView コントロールを使用してマスター/詳細形式のフォームを作成する</span><span class="sxs-lookup"><span data-stu-id="10110-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="10110-103">次のコード例では、2 つの <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドされた 2 つの <xref:System.Windows.Forms.DataGridView> コントロールを使用してマスター/詳細フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="10110-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="10110-104">データ ソースが、Northwind SQL Server のサンプル データベース、および `CustomerID` 列により 2 つに関連する <xref:System.Data.DataRelation> からの `Customers` テーブルと `Orders` テーブルを含む <xref:System.Data.DataSet> です。</span><span class="sxs-lookup"><span data-stu-id="10110-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="10110-105">1 つの <xref:System.Windows.Forms.BindingSource> はデータセットの親 `Customers` テーブルにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="10110-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="10110-106">このデータは、マスタ <xref:System.Windows.Forms.DataGridView> コントロールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="10110-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="10110-107">もう一方の <xref:System.Windows.Forms.BindingSource> は、最初のデータ コネクタにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="10110-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="10110-108">2 つ目の <xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティは、<xref:System.Data.DataRelation> の名前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="10110-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="10110-109">これにより、関連付けられている詳細の <xref:System.Windows.Forms.DataGridView> コントロールが、マスター <xref:System.Windows.Forms.DataGridView> コントロールの現在の行に対応する子の `Orders` テーブルの行を表示します。</span><span class="sxs-lookup"><span data-stu-id="10110-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="10110-110">このコード例の完全な説明については、次を参照してください。[チュートリアル:、マスター/詳細形式を使用して 2 つ Windows フォーム DataGridView コントロールを作成する](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)です。</span><span class="sxs-lookup"><span data-stu-id="10110-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10110-111">例</span><span class="sxs-lookup"><span data-stu-id="10110-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10110-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="10110-112">Compiling the Code</span></span>  
 <span data-ttu-id="10110-113">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="10110-113">This example requires:</span></span>  
  
 <span data-ttu-id="10110-114">System、System.Data、System.Windows.Forms、および System.XML の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="10110-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="10110-115">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10110-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="10110-116">また、コードを新しいプロジェクトに貼り付けることにより、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="10110-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="10110-117">参照してください[する方法: コンパイルして完成した Windows フォーム コードの例を使用して Visual Studio を実行します。](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="10110-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="10110-118">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="10110-118">.NET Framework Security</span></span>  
 <span data-ttu-id="10110-119">接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="10110-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="10110-120">データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="10110-120">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="10110-121">詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10110-121">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10110-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="10110-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="10110-123">チュートリアル: Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームの作成</span><span class="sxs-lookup"><span data-stu-id="10110-123">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="10110-124">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="10110-124">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="10110-125">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="10110-125">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
