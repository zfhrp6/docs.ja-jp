---
title: "タスク 2: ワークフロー デザイナーのホスティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# タスク 2: ワークフロー デザイナーのホスティング
このトピックでは、[!INCLUDE[avalon1](../../../includes/avalon1-md.md)] アプリケーションで [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]のインスタンスをホストする手順について説明します。  
  
 この手順では、デザイナーを格納する **Grid** コントロールを構成し、既定の <xref:System.Activities.Statements.Sequence> アクティビティを含む <xref:System.Activities.Presentation.WorkflowDesigner> のインスタンスをプログラムで作成します。さらに、デザイナーのメタデータを登録して、すべてのビルトイン アクティビティにデザイナー サポートを追加し、[!INCLUDE[avalon2](../../../includes/avalon2-md.md)] アプリケーションで[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]をホストします。  
  
### ワークフロー デザイナーをホストするには  
  
1.  「[タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)」で作成した HostingApplication プロジェクトを開きます。  
  
2.  [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] が見やすくなるように、ウィンドウのサイズを調整します。ウィンドウのサイズを調整するには、デザイナーで **\[MainWindow\]** を選択し、F4 キーを押して **\[プロパティ\]** ウィンドウを表示して、**レイアウト** セクションで **\[幅\]** の値を「600」に設定し、**\[高さ\]** の値を「350」に設定します。  
  
3.  デザイナーで **\[グリッド\]** パネルを選択し \(**\[MainWindow\]** 内のボックスをクリックします\)、**\[プロパティ\]** ウィンドウの一番上にある **Name** プロパティを「grid1」に設定して、グリッド名を設定します。  
  
4.  **\[プロパティ\]** ウィンドウで、`ColumnDefinitions` プロパティの横の省略記号 \(**\[...\]**\) をクリックして **\[コレクション エディター\]** ダイアログ ボックスを開きます。  
  
5.  **\[コレクション エディター\]** ダイアログ ボックスの **\[追加\]** ボタンを 3 回クリックして、3 つの列をレイアウトに挿入します。最初の列には **\[ツールボックス\]** が含まれ、2 番目の列は [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] をホストし、3 番目の列はプロパティ インスペクターに使用されます。  
  
6.  中央の列の `Width` プロパティの値を「4\*」に設定します。  
  
7.  **\[OK\]** をクリックして、変更を保存します。次の XAML が MainWindow.xaml ファイルに追加されます。  
  
    ```  
  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
  
    ```  
  
8.  ソリューション エクスプローラーで MainWindow.xaml を右クリックし、**\[コードの表示\]** を選択します。次の手順に従ってコードを修正します。  
  
    1.  次の名前空間を追加します。  
  
        ```csharp  
  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
  
        ```  
  
    2.  <xref:System.Activities.Presentation.WorkflowDesigner> のインスタンスを保持するプライベート メンバー フィールドを宣言するには、次のコードを `MainWindow` クラスに追加します。  
  
        ```csharp  
  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
  
        ```  
  
    3.  次の `AddDesigner` メソッドを `MainWindow` クラスに追加します。この実装で、<xref:System.Activities.Presentation.WorkflowDesigner> のインスタンスを作成し、これに <xref:System.Activities.Statements.Sequence> アクティビティを追加して、grid1 **グリッド**の中央の列に配置します。  
  
        ```csharp  
  
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
  
        ```  
  
    4.  デザイナーのメタデータを登録して、すべてのビルトイン アクティビティにデザイナー サポートを追加します。こうすることにより、ツールボックスから[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]の元の <xref:System.Activities.Statements.Sequence> アクティビティに、アクティビティをドロップできるようになります。この操作を行うには、`RegisterMetadata` メソッドを `MainWindow` クラスに追加します。  
  
        ```csharp  
  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        ```  
  
         登録アクティビティ デザイナー[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[方法: カスタム アクティビティ デザイナーを作成する](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-activity-designer.md)」を参照してください。  
  
    5.  `MainWindow` クラス コンストラクターで、前に宣言したメソッドへの呼び出しを追加して、デザイナー サポートのメタデータを登録し、<xref:System.Activities.Presentation.WorkflowDesigner> を作成します。  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
  
        ```  
  
        > [!NOTE]
        >  `RegisterMetadata` メソッドは、<xref:System.Activities.Statements.Sequence> アクティビティを含むビルトイン アクティビティのデザイナーのメタデータを登録します。`AddDesigner` メソッドは <xref:System.Activities.Statements.Sequence> アクティビティを使用するので、`RegisterMetadata` メソッドを先に呼び出す必要があります。  
  
9. F5 キーを押して、ソリューションをビルドおよび実行します。  
  
10. **\[ツールボックス\]** と **\[PropertyGrid\]** のサポートを、再ホストしたワークフロー デザイナーに追加する方法を学習するには、「[タスク 3: ツールボックス ペインと PropertyGrid ペインの作成](../../../docs/framework/windows-workflow-foundation//task-3-create-the-toolbox-and-propertygrid-panes.md)」を参照してください。  
  
## 参照  
 [ワークフロー デザイナーのホスト変更](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)   
 [タスク 3: ツールボックス ペインと PropertyGrid ペインの作成](../../../docs/framework/windows-workflow-foundation//task-3-create-the-toolbox-and-propertygrid-panes.md)