---
title: "方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73b397d750d3883bf7613756889726a52e1233cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="e69e3-102">方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする</span><span class="sxs-lookup"><span data-stu-id="e69e3-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="e69e3-103">コントロールがフォームに追加して、アプリケーションのユーザー インターフェイスを決定したら、実行時にユーザーは変更を アプリケーションに関連するデータを保存できるように、データ ソースにコントロールをバインドできます。</span><span class="sxs-lookup"><span data-stu-id="e69e3-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="e69e3-104">Windows フォーム コントロールまたは一連のコントロールのバインドが最も簡単に使用される、<xref:System.Windows.Forms.BindingSource>コントロールをフォーム上のコントロールとデータ ソース間のブリッジとして。</span><span class="sxs-lookup"><span data-stu-id="e69e3-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="e69e3-105">フォーム上の 1 つまたは複数のコントロールをデータにバインドできます。次の手順で、<xref:System.Windows.Forms.TextBox>コントロールがデータ ソースにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="e69e3-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="e69e3-106">手順を実行するには、データベースから派生したデータ ソースにバインドすると見なされます。</span><span class="sxs-lookup"><span data-stu-id="e69e3-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="e69e3-107">その他のデータのストアからデータ ソースを作成する方法の詳細については、次を参照してください。[新しいデータ ソースを追加](/visualstudio/data-tools/add-new-data-sources)です。</span><span class="sxs-lookup"><span data-stu-id="e69e3-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e69e3-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e69e3-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e69e3-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e69e3-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e69e3-110">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e69e3-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="e69e3-111">デザイン時にコントロールをバインドするには</span><span class="sxs-lookup"><span data-stu-id="e69e3-111">To bind a control at design time</span></span>  
  
1.  <span data-ttu-id="e69e3-112">ドラッグ、<xref:System.Windows.Forms.TextBox>コントロールをフォームにログオンします。</span><span class="sxs-lookup"><span data-stu-id="e69e3-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2.  <span data-ttu-id="e69e3-113">**プロパティ**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="e69e3-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="e69e3-114">展開して、 **(DataBindings)**ノード。</span><span class="sxs-lookup"><span data-stu-id="e69e3-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="e69e3-115">矢印をクリックして、次に、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e69e3-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="e69e3-116">**データソース**UI 型エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="e69e3-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="e69e3-117">プロジェクトまたはフォームのデータ ソースが構成されていた場合は、表示されます。</span><span class="sxs-lookup"><span data-stu-id="e69e3-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3.  <span data-ttu-id="e69e3-118">**[プロジェクト データ ソースの追加]** をクリックしてデータに接続し、データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4.  <span data-ttu-id="e69e3-119">**データ ソース構成ウィザード**の開始ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e69e3-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="e69e3-120">**データ ソースの種類を選択して**] ページで、[**データベース**です。</span><span class="sxs-lookup"><span data-stu-id="e69e3-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6.  <span data-ttu-id="e69e3-121">**データ接続の選択** ページで、利用可能な接続の一覧からデータ接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="e69e3-122">目的のデータ接続が表示されていない場合**新しい接続**新しいデータ接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7.  <span data-ttu-id="e69e3-123">選択**接続を [はい]、保存**をアプリケーション構成ファイルで、接続文字列を保存します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8.  <span data-ttu-id="e69e3-124">アプリケーションで使用するデータベース オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="e69e3-125">この場合、希望するテーブルのフィールドを選択、<xref:System.Windows.Forms.TextBox>を表示します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="e69e3-126">必要な場合は、既定のデータセット名を変更します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="e69e3-127">**[完了]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e69e3-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="e69e3-128">**プロパティ**ウィンドウで、矢印をクリックして、次に、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティをもう一度です。</span><span class="sxs-lookup"><span data-stu-id="e69e3-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="e69e3-129">**データソース**UI 型エディターをバインドするフィールドの名前を選択する、<xref:System.Windows.Forms.TextBox>にします。</span><span class="sxs-lookup"><span data-stu-id="e69e3-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="e69e3-130">**データソース**UI 型エディターが閉じ、データ セット<xref:System.Windows.Forms.BindingSource>およびテーブル アダプターのデータ接続が、フォームに追加されたことを特定します。</span><span class="sxs-lookup"><span data-stu-id="e69e3-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69e3-131">参照</span><span class="sxs-lookup"><span data-stu-id="e69e3-131">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="e69e3-132">新しいデータ ソースの追加</span><span class="sxs-lookup"><span data-stu-id="e69e3-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)  
 [<span data-ttu-id="e69e3-133">データ ソース ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="e69e3-133">Data Sources Window</span></span>](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
