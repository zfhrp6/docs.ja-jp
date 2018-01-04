---
title: "実行時における DynamicActivity を使用したアクティビティの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebbd6e77c2c47754054a81f4b07d3d845cdcac00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="581d1-102">実行時における DynamicActivity を使用したアクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="581d1-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="581d1-103"><xref:System.Activities.DynamicActivity> は、パブリック コンストラクターを持つ、具体的なシール クラスです。</span><span class="sxs-lookup"><span data-stu-id="581d1-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="581d1-104"><xref:System.Activities.DynamicActivity> は、実行時にアクティビティ DOM を使用してアクティビティの機能を構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="581d1-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="581d1-105">DynamicActivity の機能</span><span class="sxs-lookup"><span data-stu-id="581d1-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="581d1-106"><xref:System.Activities.DynamicActivity> は、実行プロパティ、引数、変数にアクセスできますが、子アクティビティのスケジュール設定や追跡などのランタイム サービスにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="581d1-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="581d1-107">最上位のプロパティは、ワークフローの <xref:System.Activities.Argument> オブジェクトを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="581d1-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="581d1-108">命令型コードでは、これらの引数は新しい型で CLR プロパティを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="581d1-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="581d1-109">XAML では `x:Class` タグおよび `x:Member` タグを使用して、これらの引数が宣言されます。</span><span class="sxs-lookup"><span data-stu-id="581d1-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="581d1-110"><xref:System.Activities.DynamicActivity> を使用して構築されたアクティビティは、<xref:System.ComponentModel.ICustomTypeDescriptor> を使用してデザイナーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="581d1-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="581d1-111">デザイナーで作成されたアクティビティは、次の手順に示すように、<xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> を使用して動的に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="581d1-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="581d1-112">命令型コードを使用して実行時にアクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="581d1-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="581d1-113">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="581d1-113">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="581d1-114">選択**ファイル**、**新しい**、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="581d1-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="581d1-115">選択**Workflow 4.0**  **Visual c#**で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。</span><span class="sxs-lookup"><span data-stu-id="581d1-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="581d1-116">選択**シーケンシャル ワークフロー コンソール アプリケーション**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="581d1-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="581d1-117">新しいプロジェクトに DynamicActivitySample という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="581d1-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="581d1-118">HelloActivity プロジェクトの Workflow1.xaml を右クリックし **削除**です。</span><span class="sxs-lookup"><span data-stu-id="581d1-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="581d1-119">Program.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="581d1-119">Open Program.cs.</span></span> <span data-ttu-id="581d1-120">次のディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="581d1-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="581d1-121">1 つの `Main` アクティビティを含む <xref:System.Activities.Statements.Sequence> アクティビティを作成する次のコードで <xref:System.Activities.Statements.WriteLine> メソッドの内容を置き換え、新しい動的アクティビティの <xref:System.Activities.DynamicActivity.Implementation%2A> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="581d1-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  <span data-ttu-id="581d1-122">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="581d1-122">Execute the application.</span></span> <span data-ttu-id="581d1-123">コンソール ウィンドウにテキスト"Hello World!"</span><span class="sxs-lookup"><span data-stu-id="581d1-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="581d1-124">表示されます。</span><span class="sxs-lookup"><span data-stu-id="581d1-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="581d1-125">XAML を使用して実行時にアクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="581d1-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="581d1-126">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="581d1-126">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="581d1-127">選択**ファイル**、**新しい**、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="581d1-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="581d1-128">選択**Workflow 4.0**  **Visual c#**で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。</span><span class="sxs-lookup"><span data-stu-id="581d1-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="581d1-129">選択**ワークフロー コンソール アプリケーション**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="581d1-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="581d1-130">新しいプロジェクトに DynamicActivitySample という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="581d1-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="581d1-131">HelloActivity プロジェクトの Workflow1.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="581d1-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="581d1-132">クリックして、**引数**デザイナーの下部にあるオプション。</span><span class="sxs-lookup"><span data-stu-id="581d1-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="581d1-133">`In` 型の `TextToWrite` という新しい `String` 引数を作成します。</span><span class="sxs-lookup"><span data-stu-id="581d1-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="581d1-134">ドラッグ、 **WriteLine**からアクティビティを**プリミティブ**デザイナー画面には、ツールボックスのセクションです。</span><span class="sxs-lookup"><span data-stu-id="581d1-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="581d1-135">値を割り当てる`TextToWrite`を**テキスト**アクティビティのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="581d1-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="581d1-136">Program.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="581d1-136">Open Program.cs.</span></span> <span data-ttu-id="581d1-137">次のディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="581d1-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="581d1-138">`Main` メソッドの内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="581d1-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="581d1-139">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="581d1-139">Execute the application.</span></span> <span data-ttu-id="581d1-140">コンソール ウィンドウにテキスト"Hello World!"</span><span class="sxs-lookup"><span data-stu-id="581d1-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="581d1-141">表示されます。</span><span class="sxs-lookup"><span data-stu-id="581d1-141">appears.</span></span>  
  
8.  <span data-ttu-id="581d1-142">Workflow1.xaml ファイルを右クリックし、**ソリューション エクスプ ローラー**選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="581d1-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="581d1-143">アクティビティ クラスが `x:Class` を使用して作成され、プロパティが `x:Property` を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="581d1-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581d1-144">参照</span><span class="sxs-lookup"><span data-stu-id="581d1-144">See Also</span></span>  
 [<span data-ttu-id="581d1-145">命令型コードを使用してワークフロー、アクティビティ、および式を作成する方法</span><span class="sxs-lookup"><span data-stu-id="581d1-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [<span data-ttu-id="581d1-146">DynamicActivity の作成</span><span class="sxs-lookup"><span data-stu-id="581d1-146">DynamicActivity Creation</span></span>](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
