---
title: 'タスク 3: ツールボックス ペインと PropertyGrid ペインの作成'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 9bfce22e9de1d6115cb88daddcd2dca355b6bae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519751"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="63bb8-102">タスク 3: ツールボックス ペインと PropertyGrid ペインの作成</span><span class="sxs-lookup"><span data-stu-id="63bb8-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>
<span data-ttu-id="63bb8-103">このタスクでは、作成、**ツールボックス**と**PropertyGrid**ペインに、再ホストされた追加[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="63bb8-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>  
  
 <span data-ttu-id="63bb8-104">リファレンスについては、コードを MainWindow.xaml.cs ファイルで、3 つの完了後にする必要がありますのタスクで、[ワークフロー デザイナーを再ホスト](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)一連のトピックは、このトピックの最後で提供されます。</span><span class="sxs-lookup"><span data-stu-id="63bb8-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="63bb8-105">ツールボックスを作成し、グリッドに追加するには</span><span class="sxs-lookup"><span data-stu-id="63bb8-105">To create the Toolbox and add it to the grid</span></span>  
  
1.  <span data-ttu-id="63bb8-106">説明されている手順に従って、取得した HostingApplication プロジェクトを開く[タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="63bb8-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).</span></span>  
  
2.  <span data-ttu-id="63bb8-107">**ソリューション エクスプ ローラー**  ウィンドウで、MainWindow.xaml ファイルを右クリックし、選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="63bb8-107">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
3.  <span data-ttu-id="63bb8-108">追加、`GetToolboxControl`メソッドを`MainWindow`を作成するクラス、 <xref:System.Activities.Presentation.Toolbox.ToolboxControl>、新しく追加**ツールボックス**カテゴリ、**ツールボックス**、し、割り当てます、<xref:System.Activities.Statements.Assign>と<xref:System.Activities.Statements.Sequence>アクティビティの種類をそのカテゴリ。</span><span class="sxs-lookup"><span data-stu-id="63bb8-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4.  <span data-ttu-id="63bb8-109">プライベートの追加`AddToolbox`メソッドを`MainWindow`配置クラス、**ツールボックス**グリッドで左の列にします。</span><span class="sxs-lookup"><span data-stu-id="63bb8-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  <span data-ttu-id="63bb8-110">次のコードのように、`AddToolBox` クラス コンストラクターに `MainWindow()` メソッドへの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="63bb8-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  <span data-ttu-id="63bb8-111">F5 キーを押して、ソリューションをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="63bb8-111">Press F5 to build and run your solution.</span></span> <span data-ttu-id="63bb8-112">**ツールボックス**を含む、<xref:System.Activities.Statements.Assign>と<xref:System.Activities.Statements.Sequence>アクティビティを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63bb8-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>  
  
### <a name="to-create-the-propertygrid"></a><span data-ttu-id="63bb8-113">PropertyGrid を作成するには</span><span class="sxs-lookup"><span data-stu-id="63bb8-113">To create the PropertyGrid</span></span>  
  
1.  <span data-ttu-id="63bb8-114">**ソリューション エクスプ ローラー**  ウィンドウで、MainWindow.xaml ファイルを右クリックし、選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="63bb8-114">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="63bb8-115">追加、`AddPropertyInspector`メソッドを`MainWindow`を配置するクラス、 **PropertyGrid**ウィンドウ、グリッドで一番右の列にします。</span><span class="sxs-lookup"><span data-stu-id="63bb8-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid.</span></span>  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  <span data-ttu-id="63bb8-116">次のコードのように、`AddPropertyInspector` クラス コンストラクターに `MainWindow()` メソッドへの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="63bb8-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
    ```  
  
4.  <span data-ttu-id="63bb8-117">F5 キーを押して、ソリューションをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="63bb8-117">Press F5 to build and run the solution.</span></span> <span data-ttu-id="63bb8-118">**ツールボックス**、ワークフロー デザイン キャンバス、および**PropertyGrid**ペインがすべて表示されます、およびドラッグすると、<xref:System.Activities.Statements.Assign>アクティビティまたは<xref:System.Activities.Statements.Sequence>アクティビティをデザイン キャンバスには強調表示されているアクティビティに応じてプロパティ グリッドが更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63bb8-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63bb8-119">例</span><span class="sxs-lookup"><span data-stu-id="63bb8-119">Example</span></span>  
 <span data-ttu-id="63bb8-120">MainWindow.xaml.cs ファイルに次のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="63bb8-120">The MainWindow.xaml.cs file should now contain the following code.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="63bb8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="63bb8-121">See Also</span></span>  
 [<span data-ttu-id="63bb8-122">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="63bb8-122">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="63bb8-123">タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="63bb8-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="63bb8-124">タスク 2: ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="63bb8-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
