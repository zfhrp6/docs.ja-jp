---
title: "タスク 3: ツールボックス ペインと PropertyGrid ペインの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# タスク 3: ツールボックス ペインと PropertyGrid ペインの作成
このタスクでは、**ツールボックス** ペインと **PropertyGrid** ペインを作成し、ホストを変更した [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]に追加します。  
  
 参照用として、「[ワークフロー デザイナーのホスト変更](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)」のトピック シリーズで 3 つのタスクを完了した後に MainWindow.xaml.cs ファイルに示されるコードをこのトピックの最後に示します。  
  
### ツールボックスを作成し、グリッドに追加するには  
  
1.  「[タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)」で説明されている手順に従って取得した HostingApplication プロジェクトを開きます。  
  
2.  **ソリューション エクスプローラー** ペインで、MainWindow.xaml ファイルを右クリックし、**\[コードの表示\]** をクリックします。  
  
3.  <xref:System.Activities.Presentation.Toolbox.ToolboxControl> を作成する `GetToolboxControl` メソッドを `MainWindow` クラスに追加し、新しい **Toolbox** カテゴリを **Toolbox** に追加し、<xref:System.Activities.Statements.Assign> および <xref:System.Activities.Statements.Sequence> アクティビティの種類をそのカテゴリに割り当てます。  
  
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
  
4.  グリッドの左の列に **Toolbox** を配置する `AddToolbox` プライベート メソッドを `MainWindow` クラスに追加します。  
  
    ```csharp  
  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
  
    ```  
  
5.  次のコードのように、`MainWindow()` クラス コンストラクターに `AddToolBox` メソッドへの呼び出しを追加します。  
  
    ```csharp  
  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
  
    ```  
  
6.  F5 キーを押して、ソリューションをビルドおよび実行します。<xref:System.Activities.Statements.Assign> アクティビティおよび <xref:System.Activities.Statements.Sequence> を含む **\[ツールボックス\]** が表示されます。  
  
### PropertyGrid を作成するには  
  
1.  **ソリューション エクスプローラー** ペインで、MainWindow.xaml ファイルを右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `MainWindow` クラスに `AddPropertyInspector` メソッドを追加して、グリッドの最も右側の列に **PropertyGrid** ペインを配置します。  
  
    ```csharp  
  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
  
    ```  
  
3.  次のコードのように、`MainWindow()` クラス コンストラクターに `AddPropertyInspector` メソッドへの呼び出しを追加します。  
  
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
  
4.  F5 キーを押して、ソリューションをビルドおよび実行します。**Toolbox**、ワークフロー デザイン キャンバス、および **PropertyGrid** の各ペインがすべて表示されます。また、<xref:System.Activities.Statements.Assign> アクティビティまたは <xref:System.Activities.Statements.Sequence> アクティビティをデザイン キャンバスにドラッグすると、選択されているアクティビティに応じてプロパティ グリッドが更新されます。  
  
## 使用例  
 MainWindow.xaml.cs ファイルに次のコードが含まれます。  
  
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
  
## 参照  
 [ワークフロー デザイナーのホスト変更](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)   
 [タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)