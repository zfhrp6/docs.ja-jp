---
title: .NET Framework 4 ワークフローでの相互運用アクティビティの使用
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 64e8aef01aefa23dc98b42ab835de097d6c222df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520228"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="2c377-102">.NET Framework 4 ワークフローでの相互運用アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="2c377-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="2c377-103">[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] または [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を使用して作成したアクティビティは、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティを使うことにより <xref:System.Activities.Statements.Interop> ワークフローで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c377-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="2c377-104">ここでは、<xref:System.Activities.Statements.Interop> アクティビティの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c377-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c377-105"><xref:System.Activities.Statements.Interop> 、ワークフローのプロジェクトがあるない限り、ワークフロー デザイナー ツールボックスにアクティビティが表示されないその**ターゲット フレームワーク**の設定に **.Net Framework 4**またはそれ以降。</span><span class="sxs-lookup"><span data-stu-id="2c377-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="2c377-106">.NET Framework 4.5 ワークフローでの相互運用アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="2c377-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="2c377-107">このトピックでは、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティを含む `DiscountCalculator` アクティビティ ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c377-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="2c377-108">`DiscountCalculator` は、購入額に基づいて割引を計算し、<xref:System.Workflow.Activities.SequenceActivity> を含む <xref:System.Workflow.Activities.PolicyActivity> で構成されます。</span><span class="sxs-lookup"><span data-stu-id="2c377-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c377-109">このトピックで作成する [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティでは、<xref:System.Workflow.Activities.PolicyActivity> を使用してアクティビティのロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="2c377-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="2c377-110">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ワークフローでルールを使用するためにカスタムの <xref:System.Activities.Statements.Interop> アクティビティまたは [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c377-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="2c377-111">内のルールを使用する例については、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ワークフローを使用せず、<xref:System.Activities.Statements.Interop>アクティビティを参照してください、 [.NET Framework 4.5 のポリシー アクティビティ](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="2c377-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="2c377-112">.NET Framework 3.5 アクティビティ ライブラリ プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="2c377-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="2c377-113">開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選択**新規**し**プロジェクト.**</span><span class="sxs-lookup"><span data-stu-id="2c377-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="2c377-114">**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2c377-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="2c377-115">展開、**その他のプロジェクトの種類**内のノード、**インストールされたテンプレート**ペイン**Visual Studio ソリューション**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="2c377-116">選択**空のソリューション**から、 **Visual Studio ソリューション** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2c377-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="2c377-117">型`PolicyInteropDemo`で、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="2c377-118">右クリック**PolicyInteropDemo**で**ソリューション エクスプ ローラー**選択**追加**し**新しいプロジェクト**.</span><span class="sxs-lookup"><span data-stu-id="2c377-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="2c377-119">場合、**ソリューション エクスプ ローラー**ウィンドウが表示されている、select**ソリューション エクスプ ローラー**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2c377-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="2c377-120">**インストールされたテンプレート**一覧で、 **Visual c#** し**ワークフロー**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="2c377-121">選択 **.NET Framework 3.5**クリックして .NET Framework のバージョンのドロップダウン リストから**Workflow Activity Library**から、**テンプレート** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2c377-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="2c377-122">型`PolicyActivityLibrary`で、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="2c377-123">右クリック**Activity1.cs**で**ソリューション エクスプ ローラー**選択**削除**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="2c377-124">**[OK]** をクリックして確定します。</span><span class="sxs-lookup"><span data-stu-id="2c377-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="2c377-125">DiscountCalculator アクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="2c377-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="2c377-126">右クリック**PolicyActivityLibrary**で**ソリューション エクスプ ローラー**選択**追加**し**アクティビティ**.</span><span class="sxs-lookup"><span data-stu-id="2c377-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="2c377-127">選択**アクティビティ (コード分離付き)** から、 **Visual c# アイテム** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2c377-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="2c377-128">型`DiscountCalculator`で、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="2c377-129">右クリック**DiscountCalculator.xoml**で**ソリューション エクスプ ローラー**選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="2c377-130">`DiscountCalculator` クラスに次の 3 つのプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c377-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="2c377-131">右クリック**DiscountCalculator.xoml**で**ソリューション エクスプ ローラー**選択**ビュー デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="2c377-132">ドラッグ、**ポリシー**からアクティビティを**Windows Workflow v3.0**のセクションで、**ツールボックス**内にドロップし、 **DiscountCalculator**アクティビティ.</span><span class="sxs-lookup"><span data-stu-id="2c377-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="2c377-133">場合、**ツールボックス**ウィンドウが表示されている、select**ツールボックス**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2c377-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="2c377-134">ルールを構成するには</span><span class="sxs-lookup"><span data-stu-id="2c377-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="2c377-135">クリックして、新しく追加した**ポリシー**してが選択されていない場合に選択し、アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2c377-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="2c377-136">クリックして、 **RuleSetReference**プロパティに、**プロパティ**ウィンドウを選択し、プロパティの右側にある省略記号ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c377-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="2c377-137">場合、**プロパティ**ウィンドウが表示されていない、選択**プロパティ ウィンドウ**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="2c377-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="2c377-138">選択**新規 をクリックしています**.</span><span class="sxs-lookup"><span data-stu-id="2c377-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="2c377-139">をクリックして**規則の追加**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="2c377-140">次の式を入力、**条件**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="2c377-141">次の式を入力、 **Then アクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="2c377-142">をクリックして**規則の追加**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="2c377-143">次の式を入力、**条件**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="2c377-144">次の式を入力、 **Then アクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="2c377-145">をクリックして**規則の追加**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="2c377-146">次の式を入力、**条件**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="2c377-147">次の式を入力、 **Then アクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="2c377-148">次の式を入力、 **Else アクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="2c377-149">をクリックして**OK**を閉じる、**ルール セット エディター**  ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="2c377-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="2c377-150">新たに作成されたことを確認<xref:System.Workflow.Activities.Rules.RuleSet>でが選択されている、**名前**ボックスの一覧し、をクリックして **[ok]** です。</span><span class="sxs-lookup"><span data-stu-id="2c377-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="2c377-151">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="2c377-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="2c377-152">この手順で `DiscountCalculator` アクティビティに追加したルールを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="2c377-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="2c377-153"><xref:System.Workflow.Activities.PolicyActivity> を実行すると、これら 3 つのルールによって、`Subtotal` アクティビティの `DiscountPercent`、`Total`、および `DiscountCalculator` の各プロパティ値が評価および変更され、目的の割引が計算されます。</span><span class="sxs-lookup"><span data-stu-id="2c377-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="2c377-154">DiscountCalculator アクティビティと相互運用アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="2c377-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="2c377-155">`DiscountCalculator` ワークフロー内で [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティを使用するには、<xref:System.Activities.Statements.Interop> アクティビティを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c377-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="2c377-156">ここでは、2 つのワークフローを作成します。1 つはコードを使用し、1 つはワークフロー デザイナーを使用します。また、<xref:System.Activities.Statements.Interop> アクティビティと `DiscountCalculator` アクティビティを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c377-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="2c377-157">両方のワークフローに同じホスト アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c377-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="2c377-158">ホスト アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="2c377-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="2c377-159">右クリック**PolicyInteropDemo**で**ソリューション エクスプ ローラー**選択**追加**、し**新しいプロジェクト**.</span><span class="sxs-lookup"><span data-stu-id="2c377-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="2c377-160">いることを確認 **.NET Framework 4.5** .NET Framework のバージョンのドロップダウン リストで選択され、選択**ワークフロー コンソール アプリケーション**から、 **Visual c# アイテム** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2c377-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="2c377-161">型`PolicyInteropHost`に、**名前**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="2c377-162">右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="2c377-163">**ターゲット フレームワーク**ドロップダウン ボックスの一覧で選択を変更するから **.NET Framework 4 Client Profile**に **.NET Framework 4.5**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="2c377-164">をクリックして**はい**ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c377-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="2c377-165">右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**参照の追加**.</span><span class="sxs-lookup"><span data-stu-id="2c377-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="2c377-166">選択**PolicyActivityLibrary**から、**プロジェクト** タブでをクリックし、 **OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="2c377-167">右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**参照の追加**.</span><span class="sxs-lookup"><span data-stu-id="2c377-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="2c377-168">選択**System.Workflow.Activities**、 **System.Workflow.ComponentModel**、し**System.Workflow.Runtime**から、 **.NET** タブでをクリックし、 **OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="2c377-169">右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="2c377-170">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="2c377-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="2c377-171">コードでの Interop アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="2c377-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="2c377-172">この例では、<xref:System.Activities.Statements.Interop> アクティビティおよび `DiscountCalculator` アクティビティを含むコードを使用して、ワークフロー定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="2c377-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="2c377-173">このワークフローは、<xref:System.Activities.WorkflowInvoker> を使用して呼び出され、ルールの評価結果は、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2c377-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="2c377-174">コードで Interop アクティビティを使用するには</span><span class="sxs-lookup"><span data-stu-id="2c377-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="2c377-175">右クリック**Program.cs**で**ソリューション エクスプ ローラー**選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="2c377-176">ファイルの先頭に次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c377-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="2c377-177">`Main` メソッドの内容を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2c377-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="2c377-178">次のコードを含む `Program` と呼ばれる `CalculateDiscountUsingCodeWorkflow` クラスで新しいメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c377-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2c377-179">`Subtotal` アクティビティの `DiscountPercent`、`Total`、および `DiscountCalculator` プロパティは <xref:System.Activities.Statements.Interop> アクティビティの引数として表示され、<xref:System.Activities.Statements.Interop> アクティビティの <xref:System.Activities.Statements.Interop.ActivityProperties%2A> コレクションのローカル ワークフロー変数にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="2c377-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="2c377-180">`Subtotal` データは <xref:System.Activities.ArgumentDirection.In> アクティビティへ追加されるので、`Subtotal` は <xref:System.Activities.Statements.Interop> 引数として追加されます。`DiscountPercent` と `Total` は、<xref:System.Activities.ArgumentDirection.Out> アクティビティから出力されるデータであるので、<xref:System.Activities.Statements.Interop> 引数として追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c377-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="2c377-181">2 つの <xref:System.Activities.ArgumentDirection.Out> 引数は、`DiscountPercentOut` 引数を表すことを示すために、`TotalOut` および <xref:System.Activities.ArgumentDirection.Out> という名前で追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c377-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="2c377-182">`DiscountCalculator` タイプは、<xref:System.Activities.Statements.Interop> アクティビティの <xref:System.Activities.Statements.Interop.ActivityType%2A> として指定されます。</span><span class="sxs-lookup"><span data-stu-id="2c377-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="2c377-183">Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c377-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="2c377-184">`Subtotal` 値を異なる値に置き換え、`DiscountCalculator` アクティビティに用意されているさまざまな割引レベルをテストします。</span><span class="sxs-lookup"><span data-stu-id="2c377-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="2c377-185">ワークフロー デザイナーでの Interop アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="2c377-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="2c377-186">この例では、ワークフロー デザイナーを使用してワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c377-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="2c377-187">このワークフローは前の例と同じ機能ですが、<xref:System.Activities.Statements.WriteLine> を使用して割引を表示するのではなく、ワークフローの完了時にホスト アプリケーションで割引情報を取得および表示するという点が異なります。</span><span class="sxs-lookup"><span data-stu-id="2c377-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="2c377-188">また、データを含むローカル ワークフロー変数を使用するのではなく、ワークフローの呼び出し時に、引数がワークフロー デザイナーで作成され、値はホストから渡されます。</span><span class="sxs-lookup"><span data-stu-id="2c377-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="2c377-189">ワークフロー デザイナーで作成したワークフローを使用して PolicyActivity をホストするには</span><span class="sxs-lookup"><span data-stu-id="2c377-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="2c377-190">右クリック**Workflow1.xaml**で**ソリューション エクスプ ローラー**選択**削除**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="2c377-191">**[OK]** をクリックして確定します。</span><span class="sxs-lookup"><span data-stu-id="2c377-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="2c377-192">右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加**.</span><span class="sxs-lookup"><span data-stu-id="2c377-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="2c377-193">展開して、 **Visual c# アイテム**ノード**ワークフロー**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="2c377-194">選択**アクティビティ**から、 **Visual c# アイテム** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2c377-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="2c377-195">型`DiscountWorkflow`に、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="2c377-196">クリックして、**引数**を表示するワークフロー デザイナーの左下のボタン、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2c377-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="2c377-197">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="2c377-198">型`Subtotal`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**二重**から**引数の型**ドロップ ダウンし、enter キーを押して引数を保存します。</span><span class="sxs-lookup"><span data-stu-id="2c377-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2c377-199">場合**二重**に含まれていない、**引数の型**ドロップダウン リストで、**型を参照しています.**、型`System.Double`で、**型名**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="2c377-200">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="2c377-201">型`DiscountPercent`に、**名前**ボックスで、**アウト**から、**方向**ドロップダウン リストで、**二重**から**引数の型**ドロップ ダウンし、enter キーを押して引数を保存します。</span><span class="sxs-lookup"><span data-stu-id="2c377-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="2c377-202">をクリックして**引数の作成**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="2c377-203">型`Total`に、**名前**ボックスで、**アウト**から、**方向**ドロップダウン リストで、**二重**から**引数の型**ドロップ ダウンし、enter キーを押して引数を保存します。</span><span class="sxs-lookup"><span data-stu-id="2c377-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="2c377-204">クリックして、**引数**を閉じる、ワークフロー デザイナーの左下のボタン、**引数**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2c377-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="2c377-205">ドラッグ、**シーケンス**からアクティビティを**制御フロー**のセクションで、**ツールボックス**し、ワークフロー デザイナー画面にドロップします。</span><span class="sxs-lookup"><span data-stu-id="2c377-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="2c377-206">ドラッグ、**相互運用機能**からアクティビティを**移行**のセクションで、**ツールボックス**内にドロップし、**シーケンス**アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="2c377-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="2c377-207">クリックして、**相互運用機能**上のアクティビティ、 **[参照] をクリックしています.**</span><span class="sxs-lookup"><span data-stu-id="2c377-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="2c377-208">ラベルを入力**DiscountCalculator**で、**型名**ボックスし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2c377-209"><xref:System.Activities.Statements.Interop> アクティビティをワークフローに追加し、`DiscountCalculator` 型を <xref:System.Activities.Statements.Interop.ActivityType%2A> として指定すると、<xref:System.Activities.Statements.Interop> アクティビティは 3 つの <xref:System.Activities.ArgumentDirection.In> 引数と 3 つの <xref:System.Activities.ArgumentDirection.Out> 引数を公開します。これは `DiscountCalculator` アクティビティの 3 つのパブリック プロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="2c377-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="2c377-210"><xref:System.Activities.ArgumentDirection.In>引数は、3 つのパブリック プロパティと、3 つと同じ名前を付ける<xref:System.Activities.ArgumentDirection.Out>引数と一致する名前がある**アウト**プロパティ名に付加します。</span><span class="sxs-lookup"><span data-stu-id="2c377-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="2c377-211">次の手順では、前の手順で作成したワークフロー引数を、<xref:System.Activities.Statements.Interop> アクティビティの引数にバインドします。</span><span class="sxs-lookup"><span data-stu-id="2c377-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="2c377-212">型`DiscountPercent`に、 **VB の式を入力**の右側のボックスに、 **DiscountPercentOut**プロパティと TAB キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2c377-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="2c377-213">型`Subtotal`に、 **VB の式を入力**の右側のボックスに、 **Subtotal**プロパティと TAB キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2c377-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="2c377-214">型`Total`に、 **VB の式を入力**の右側のボックスに、 **TotalOut**プロパティと TAB キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2c377-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="2c377-215">右クリック**Program.cs**で**ソリューション エクスプ ローラー**選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="2c377-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="2c377-216">ファイルの先頭に次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c377-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="2c377-217">`CalculateDiscountInCode` メソッドに含まれる `Main` メソッドの呼び出しをコメント アウトし、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c377-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2c377-218">前の手順を実行せず、既定の `Main` コードのままの場合、`Main` の内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2c377-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="2c377-219">次のコードを含む `Program` と呼ばれる `CalculateDiscountUsingDesignerWorkflow` クラスで新しいメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c377-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. <span data-ttu-id="2c377-220">Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2c377-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="2c377-221">異なる `Subtotal` の額を指定するには、次のコードの `SubtotalValue` 値を変更します。</span><span class="sxs-lookup"><span data-stu-id="2c377-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="2c377-222">ルール機能の概要</span><span class="sxs-lookup"><span data-stu-id="2c377-222">Rules Features Overview</span></span>  
 <span data-ttu-id="2c377-223">[!INCLUDE[wf1](../../../includes/wf1-md.md)] ルール エンジンは、フォワード チェーンをサポートする優先順位に基づく方法で、ルールの処理をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2c377-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="2c377-224">単一のアイテムまたはコレクション内のアイテムについて、ルールを評価できます。</span><span class="sxs-lookup"><span data-stu-id="2c377-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="2c377-225">ルールの概要および特定のルール機能に関する情報については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c377-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="2c377-226">ルール機能</span><span class="sxs-lookup"><span data-stu-id="2c377-226">Rules Feature</span></span>|<span data-ttu-id="2c377-227">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2c377-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="2c377-228">ルールの概要</span><span class="sxs-lookup"><span data-stu-id="2c377-228">Rules Overview</span></span>|[<span data-ttu-id="2c377-229">Windows Workflow Foundation ルール エンジンの概要</span><span class="sxs-lookup"><span data-stu-id="2c377-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="2c377-230">RuleSet</span><span class="sxs-lookup"><span data-stu-id="2c377-230">RuleSet</span></span>|<span data-ttu-id="2c377-231">[ワークフローでの RuleSets の使用](http://go.microsoft.com/fwlink/?LinkId=178516)と <xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="2c377-231">[Using RuleSets in Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="2c377-232">ルールの評価</span><span class="sxs-lookup"><span data-stu-id="2c377-232">Evaluation of Rules</span></span>|[<span data-ttu-id="2c377-233">RuleSets 内のルールの評価</span><span class="sxs-lookup"><span data-stu-id="2c377-233">Rules Evaluation in RuleSets</span></span>](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="2c377-234">ルール チェーン</span><span class="sxs-lookup"><span data-stu-id="2c377-234">Rules Chaining</span></span>|<span data-ttu-id="2c377-235">[フォワード チェーン コントロール](http://go.microsoft.com/fwlink/?LinkId=178518)と[ルールのフォワード チェーン](http://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="2c377-235">[Forward Chaining Control](http://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](http://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="2c377-236">ルール内コレクションの処理</span><span class="sxs-lookup"><span data-stu-id="2c377-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="2c377-237">ルール内コレクションの処理</span><span class="sxs-lookup"><span data-stu-id="2c377-237">Processing Collections in Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="2c377-238">PolicyActivity の使用</span><span class="sxs-lookup"><span data-stu-id="2c377-238">Using the PolicyActivity</span></span>|<span data-ttu-id="2c377-239">[PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink/?LinkId=178521)と <xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="2c377-239">[Using the PolicyActivity Activity](http://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="2c377-240">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] で作成したワークフローでは、たとえば宣言的アクティビティ条件や条件付きアクティビティ ([!INCLUDE[wf1](../../../includes/wf1-md.md)]、<xref:System.Workflow.Activities.ConditionedActivityGroup> など) など、<xref:System.Workflow.Activities.ReplicatorActivity> に用意されているルール機能のすべてを使用するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2c377-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="2c377-241">必要に応じて、この機能は [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] および [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を使用して作成したワークフローに使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c377-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="2c377-242">詳細については、次を参照してください。[移行ガイダンス](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c377-242">For more information, see [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>
