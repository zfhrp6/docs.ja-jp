---
title: "方法 : デザイナーを使って Windows フォーム コントロールを型にバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee932e7cb4a3333ac56242e281ec64d3016746f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="59ca8-102">方法 : デザイナーを使って Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="59ca8-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="59ca8-103">データをやり取りするコントロールを作成する際、オブジェクトではなく型にコントロールをバインドすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="59ca8-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="59ca8-104">データを使用できないが、データ バインド コントロールで型のパブリック インターフェイスからデータを表示する必要がある場合、通常はデザイン時にコントロールを型にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ca8-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="59ca8-105">次の手順を新規作成する方法を説明する<xref:System.Windows.Forms.BindingSource>されている型にバインドし、型のプロパティのいずれかにバインドする方法、<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="59ca8-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="59ca8-106">BindingSource を型にバインドするには</span><span class="sxs-lookup"><span data-stu-id="59ca8-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="59ca8-107">Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="59ca8-107">Create a Windows Forms project.</span></span>  
  
     <span data-ttu-id="59ca8-108">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ca8-108">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="59ca8-109">**デザイン**ビューで、ドラッグ、<xref:System.Windows.Forms.BindingSource>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="59ca8-109">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="59ca8-110">**プロパティ**ウィンドウで、矢印をクリックして、<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59ca8-110">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="59ca8-111">**DataSource UI 型エディター**で、**[プロジェクト データ ソースの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59ca8-111">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="59ca8-112">**[データ ソースの種類を選択]** ページで、**[オブジェクト]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59ca8-112">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="59ca8-113">バインド先となる型を選択します。</span><span class="sxs-lookup"><span data-stu-id="59ca8-113">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="59ca8-114">バインド先となる型が現在のプロジェクトにある場合、または、型を含むアセンブリが参照として既に追加されている場合は、ノードを展開し、目的の型を探して選択します。</span><span class="sxs-lookup"><span data-stu-id="59ca8-114">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="59ca8-115">- または -</span><span class="sxs-lookup"><span data-stu-id="59ca8-115">-or-</span></span>  
  
    -   <span data-ttu-id="59ca8-116">バインド先となる型が、現在、参照の一覧にはなく、別のアセンブリにある場合は、**[参照の追加]** をクリックして **[プロジェクト]** タブをクリックします。目的のビジネス オブジェクトを含むプロジェクトを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59ca8-116">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="59ca8-117">このプロジェクトは、アセンブリの一覧に表示されるため、ノードを展開し、目的の型を探して選択します。</span><span class="sxs-lookup"><span data-stu-id="59ca8-117">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="59ca8-118">フレームワークまたは Microsoft アセンブリの型にバインドする場合は、**[Microsoft または System で始まるアセンブリを表示しない]** チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="59ca8-118">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="59ca8-119">**[次へ]**をクリックし、 **[完了]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59ca8-119">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="59ca8-120">コントロールを BindingSource にバインドするには</span><span class="sxs-lookup"><span data-stu-id="59ca8-120">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="59ca8-121">フォームに <xref:System.Windows.Forms.TextBox> を追加します。</span><span class="sxs-lookup"><span data-stu-id="59ca8-121">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="59ca8-122">**[プロパティ]** ウィンドウで **(DataBindings)** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="59ca8-122">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="59ca8-123">矢印をクリックして、次に、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59ca8-123">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="59ca8-124">**データ ソースの UI 型エディター**、ノードを展開します、<xref:System.Windows.Forms.BindingSource>以前は、追加され、プロパティにバインドするバインドの種類の選択、<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="59ca8-124">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ca8-125">参照</span><span class="sxs-lookup"><span data-stu-id="59ca8-125">See Also</span></span>  
 [<span data-ttu-id="59ca8-126">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="59ca8-126">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="59ca8-127">方法: Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="59ca8-127">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="59ca8-128">Visual Studio でのデータへのコントロールのバインド</span><span class="sxs-lookup"><span data-stu-id="59ca8-128">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
