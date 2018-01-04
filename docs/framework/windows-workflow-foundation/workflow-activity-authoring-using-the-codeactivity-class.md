---
title: "CodeActivity クラスを使用したワークフロー アクティビティの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2daec260c1224cd81280c6bf699b70efc2072588
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="c6d4c-102">CodeActivity クラスを使用したワークフロー アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="c6d4c-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="c6d4c-103"><xref:System.Activities.CodeActivity> を継承して作成されたアクティビティは、<xref:System.Activities.CodeActivity.Execute%2A> メソッドをオーバーライドすることで強制的な基本動作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-codeactivitycontext"></a><span data-ttu-id="c6d4c-104">CodeActivityContext の使用</span><span class="sxs-lookup"><span data-stu-id="c6d4c-104">Using CodeActivityContext</span></span>  
 <span data-ttu-id="c6d4c-105">ワークフロー ランタイムの機能は、<xref:System.Activities.CodeActivity.Execute%2A> 型の `context` パラメーターを使用して、<xref:System.Activities.CodeActivityContext> メソッド内からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="c6d4c-106"><xref:System.Activities.CodeActivityContext> を介して、以下のような機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="c6d4c-107">変数と引数の値を取得および設定。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-107">Getting and setting the values of variables and arguments.</span></span>  
  
-   <span data-ttu-id="c6d4c-108"><xref:System.Activities.CodeActivityContext.Track%2A> を使用したカスタムの追跡機能。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="c6d4c-109"><xref:System.Activities.CodeActivityContext.GetProperty%2A> を使用したアクティビティの実行プロパティへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="c6d4c-110">CodeActivity を継承するカスタム アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="c6d4c-110">To create a custom activity that inherits from CodeActivity</span></span>  
  
1.  <span data-ttu-id="c6d4c-111">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-111">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c6d4c-112">選択**ファイル**、**新しい**、し**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="c6d4c-113">選択**Workflow 4.0**  **Visual c#**で、**プロジェクトの種類**ウィンドウ、および選択、 **v2010**ノード。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="c6d4c-114">選択**アクティビティ ライブラリ**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="c6d4c-115">新しいプロジェクトに HelloActivity という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-115">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="c6d4c-116">HelloActivity プロジェクトの Activity1.xaml を右クリックし **削除**です。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="c6d4c-117">HelloActivity プロジェクトを右クリックし **追加**、し**クラス**です。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="c6d4c-118">新しいクラスに HelloActivity.cs という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-118">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="c6d4c-119">HelloActivity.cs ファイルで、次の `using` ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="c6d4c-120">クラス宣言に基本クラスを追加することにより、新しいクラスで <xref:System.Activities.CodeActivity> から継承します。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  <span data-ttu-id="c6d4c-121"><xref:System.Activities.CodeActivity.Execute%2A> メソッドを追加して、このクラスに機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="c6d4c-122"><xref:System.Activities.CodeActivityContext> を使用して追跡レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="c6d4c-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
