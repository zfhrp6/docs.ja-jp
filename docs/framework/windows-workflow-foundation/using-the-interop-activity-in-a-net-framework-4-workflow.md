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
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>.NET Framework 4 ワークフローでの相互運用アクティビティの使用
[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] または [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を使用して作成したアクティビティは、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティを使うことにより <xref:System.Activities.Statements.Interop> ワークフローで使用できます。 ここでは、<xref:System.Activities.Statements.Interop> アクティビティの概要について説明します。  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> 、ワークフローのプロジェクトがあるない限り、ワークフロー デザイナー ツールボックスにアクティビティが表示されないその**ターゲット フレームワーク**の設定に **.Net Framework 4**またはそれ以降。  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>.NET Framework 4.5 ワークフローでの相互運用アクティビティの使用  
 このトピックでは、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティを含む `DiscountCalculator` アクティビティ ライブラリを作成します。 `DiscountCalculator` は、購入額に基づいて割引を計算し、<xref:System.Workflow.Activities.SequenceActivity> を含む <xref:System.Workflow.Activities.PolicyActivity> で構成されます。  
  
> [!NOTE]
>  このトピックで作成する [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティでは、<xref:System.Workflow.Activities.PolicyActivity> を使用してアクティビティのロジックを実装します。 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ワークフローでルールを使用するためにカスタムの <xref:System.Activities.Statements.Interop> アクティビティまたは [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティを使用する必要はありません。 内のルールを使用する例については、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ワークフローを使用せず、<xref:System.Activities.Statements.Interop>アクティビティを参照してください、 [.NET Framework 4.5 のポリシー アクティビティ](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md)サンプルです。  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>.NET Framework 3.5 アクティビティ ライブラリ プロジェクトを作成するには  
  
1.  開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選択**新規**し**プロジェクト.** **ファイル**メニュー。  
  
2.  展開、**その他のプロジェクトの種類**内のノード、**インストールされたテンプレート**ペイン**Visual Studio ソリューション**です。  
  
3.  選択**空のソリューション**から、 **Visual Studio ソリューション** ボックスの一覧です。 型`PolicyInteropDemo`で、**名前**ボックスし、をクリックして**OK**です。  
  
4.  右クリック**PolicyInteropDemo**で**ソリューション エクスプ ローラー**選択**追加**し**新しいプロジェクト**.  
  
    > [!TIP]
    >  場合、**ソリューション エクスプ ローラー**ウィンドウが表示されている、select**ソリューション エクスプ ローラー**から、**ビュー**メニュー。  
  
5.  **インストールされたテンプレート**一覧で、 **Visual c#** し**ワークフロー**です。 選択 **.NET Framework 3.5**クリックして .NET Framework のバージョンのドロップダウン リストから**Workflow Activity Library**から、**テンプレート** ボックスの一覧です。  
  
6.  型`PolicyActivityLibrary`で、**名前**ボックスし、をクリックして**OK**です。  
  
7.  右クリック**Activity1.cs**で**ソリューション エクスプ ローラー**選択**削除**です。 **[OK]** をクリックして確定します。  
  
#### <a name="to-create-the-discountcalculator-activity"></a>DiscountCalculator アクティビティを作成するには  
  
1.  右クリック**PolicyActivityLibrary**で**ソリューション エクスプ ローラー**選択**追加**し**アクティビティ**.  
  
2.  選択**アクティビティ (コード分離付き)** から、 **Visual c# アイテム** ボックスの一覧です。 型`DiscountCalculator`で、**名前**ボックスし、をクリックして**OK**です。  
  
3.  右クリック**DiscountCalculator.xoml**で**ソリューション エクスプ ローラー**選択**コードの表示**です。  
  
4.  `DiscountCalculator` クラスに次の 3 つのプロパティを追加します。  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  右クリック**DiscountCalculator.xoml**で**ソリューション エクスプ ローラー**選択**ビュー デザイナー**です。  
  
6.  ドラッグ、**ポリシー**からアクティビティを**Windows Workflow v3.0**のセクションで、**ツールボックス**内にドロップし、 **DiscountCalculator**アクティビティ.  
  
    > [!TIP]
    >  場合、**ツールボックス**ウィンドウが表示されている、select**ツールボックス**から、**ビュー**メニュー。  
  
#### <a name="to-configure-the-rules"></a>ルールを構成するには  
  
1.  クリックして、新しく追加した**ポリシー**してが選択されていない場合に選択し、アクティビティ。  
  
2.  クリックして、 **RuleSetReference**プロパティに、**プロパティ**ウィンドウを選択し、プロパティの右側にある省略記号ボタンをクリックします。  
  
    > [!TIP]
    >  場合、**プロパティ**ウィンドウが表示されていない、選択**プロパティ ウィンドウ**から、**ビュー**メニュー。  
  
3.  選択**新規 をクリックしています**.  
  
4.  をクリックして**規則の追加**です。  
  
5.  次の式を入力、**条件**ボックス。  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  次の式を入力、 **Then アクション**ボックス。  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  をクリックして**規則の追加**です。  
  
8.  次の式を入力、**条件**ボックス。  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. 次の式を入力、 **Then アクション**ボックス。  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. をクリックして**規則の追加**です。  
  
11. 次の式を入力、**条件**ボックス。  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. 次の式を入力、 **Then アクション**ボックス。  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. 次の式を入力、 **Else アクション**ボックス。  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. をクリックして**OK**を閉じる、**ルール セット エディター**  ダイアログ ボックス。  
  
15. 新たに作成されたことを確認<xref:System.Workflow.Activities.Rules.RuleSet>でが選択されている、**名前**ボックスの一覧し、をクリックして **[ok]** です。  
  
16. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
 この手順で `DiscountCalculator` アクティビティに追加したルールを次のコード例に示します。  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <xref:System.Workflow.Activities.PolicyActivity> を実行すると、これら 3 つのルールによって、`Subtotal` アクティビティの `DiscountPercent`、`Total`、および `DiscountCalculator` の各プロパティ値が評価および変更され、目的の割引が計算されます。  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>DiscountCalculator アクティビティと相互運用アクティビティの使用  
 `DiscountCalculator` ワークフロー内で [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] アクティビティを使用するには、<xref:System.Activities.Statements.Interop> アクティビティを使用します。 ここでは、2 つのワークフローを作成します。1 つはコードを使用し、1 つはワークフロー デザイナーを使用します。また、<xref:System.Activities.Statements.Interop> アクティビティと `DiscountCalculator` アクティビティを使用する方法について説明します。 両方のワークフローに同じホスト アプリケーションを使用します。  
  
#### <a name="to-create-the-host-application"></a>ホスト アプリケーションを作成するには  
  
1.  右クリック**PolicyInteropDemo**で**ソリューション エクスプ ローラー**選択**追加**、し**新しいプロジェクト**.  
  
2.  いることを確認 **.NET Framework 4.5** .NET Framework のバージョンのドロップダウン リストで選択され、選択**ワークフロー コンソール アプリケーション**から、 **Visual c# アイテム** ボックスの一覧です。  
  
3.  型`PolicyInteropHost`に、**名前**ボックスし、をクリックして**OK**です。  
  
4.  右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**プロパティ**です。  
  
5.  **ターゲット フレームワーク**ドロップダウン ボックスの一覧で選択を変更するから **.NET Framework 4 Client Profile**に **.NET Framework 4.5**です。 をクリックして**はい**ことを確認します。  
  
6.  右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**参照の追加**.  
  
7.  選択**PolicyActivityLibrary**から、**プロジェクト** タブでをクリックし、 **OK**です。  
  
8.  右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**参照の追加**.  
  
9. 選択**System.Workflow.Activities**、 **System.Workflow.ComponentModel**、し**System.Workflow.Runtime**から、 **.NET** タブでをクリックし、 **OK**です。  
  
10. 右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**です。  
  
11. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
### <a name="using-the-interop-activity-in-code"></a>コードでの Interop アクティビティの使用  
 この例では、<xref:System.Activities.Statements.Interop> アクティビティおよび `DiscountCalculator` アクティビティを含むコードを使用して、ワークフロー定義を作成します。 このワークフローは、<xref:System.Activities.WorkflowInvoker> を使用して呼び出され、ルールの評価結果は、<xref:System.Activities.Statements.WriteLine> アクティビティを使用してコンソールに書き込まれます。  
  
##### <a name="to-use-the-interop-activity-in-code"></a>コードで Interop アクティビティを使用するには  
  
1.  右クリック**Program.cs**で**ソリューション エクスプ ローラー**選択**コードの表示**です。  
  
2.  ファイルの先頭に次の `using` ステートメントを追加します。  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  `Main` メソッドの内容を削除し、次のコードに置き換えます。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  次のコードを含む `Program` と呼ばれる `CalculateDiscountUsingCodeWorkflow` クラスで新しいメソッドを作成します。  
  
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
    >  `Subtotal` アクティビティの `DiscountPercent`、`Total`、および `DiscountCalculator` プロパティは <xref:System.Activities.Statements.Interop> アクティビティの引数として表示され、<xref:System.Activities.Statements.Interop> アクティビティの <xref:System.Activities.Statements.Interop.ActivityProperties%2A> コレクションのローカル ワークフロー変数にバインドされます。 `Subtotal` データは <xref:System.Activities.ArgumentDirection.In> アクティビティへ追加されるので、`Subtotal` は <xref:System.Activities.Statements.Interop> 引数として追加されます。`DiscountPercent` と `Total` は、<xref:System.Activities.ArgumentDirection.Out> アクティビティから出力されるデータであるので、<xref:System.Activities.Statements.Interop> 引数として追加されます。 2 つの <xref:System.Activities.ArgumentDirection.Out> 引数は、`DiscountPercentOut` 引数を表すことを示すために、`TotalOut` および <xref:System.Activities.ArgumentDirection.Out> という名前で追加されます。 `DiscountCalculator` タイプは、<xref:System.Activities.Statements.Interop> アクティビティの <xref:System.Activities.Statements.Interop.ActivityType%2A> として指定されます。  
  
5.  Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。 `Subtotal` 値を異なる値に置き換え、`DiscountCalculator` アクティビティに用意されているさまざまな割引レベルをテストします。  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>ワークフロー デザイナーでの Interop アクティビティの使用  
 この例では、ワークフロー デザイナーを使用してワークフローを作成します。 このワークフローは前の例と同じ機能ですが、<xref:System.Activities.Statements.WriteLine> を使用して割引を表示するのではなく、ワークフローの完了時にホスト アプリケーションで割引情報を取得および表示するという点が異なります。 また、データを含むローカル ワークフロー変数を使用するのではなく、ワークフローの呼び出し時に、引数がワークフロー デザイナーで作成され、値はホストから渡されます。  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>ワークフロー デザイナーで作成したワークフローを使用して PolicyActivity をホストするには  
  
1.  右クリック**Workflow1.xaml**で**ソリューション エクスプ ローラー**選択**削除**です。 **[OK]** をクリックして確定します。  
  
2.  右クリック**PolicyInteropHost**で**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加**.  
  
3.  展開して、 **Visual c# アイテム**ノード**ワークフロー**です。 選択**アクティビティ**から、 **Visual c# アイテム** ボックスの一覧です。  
  
4.  型`DiscountWorkflow`に、**名前**ボックスし、をクリックして**追加**です。  
  
5.  クリックして、**引数**を表示するワークフロー デザイナーの左下のボタン、**引数**ウィンドウです。  
  
6.  をクリックして**引数の作成**です。  
  
7.  型`Subtotal`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**二重**から**引数の型**ドロップ ダウンし、enter キーを押して引数を保存します。  
  
    > [!NOTE]
    >  場合**二重**に含まれていない、**引数の型**ドロップダウン リストで、**型を参照しています.**、型`System.Double`で、**型名**ボックスし、をクリックして**OK**です。  
  
8.  をクリックして**引数の作成**です。  
  
9. 型`DiscountPercent`に、**名前**ボックスで、**アウト**から、**方向**ドロップダウン リストで、**二重**から**引数の型**ドロップ ダウンし、enter キーを押して引数を保存します。  
  
10. をクリックして**引数の作成**です。  
  
11. 型`Total`に、**名前**ボックスで、**アウト**から、**方向**ドロップダウン リストで、**二重**から**引数の型**ドロップ ダウンし、enter キーを押して引数を保存します。  
  
12. クリックして、**引数**を閉じる、ワークフロー デザイナーの左下のボタン、**引数**ウィンドウです。  
  
13. ドラッグ、**シーケンス**からアクティビティを**制御フロー**のセクションで、**ツールボックス**し、ワークフロー デザイナー画面にドロップします。  
  
14. ドラッグ、**相互運用機能**からアクティビティを**移行**のセクションで、**ツールボックス**内にドロップし、**シーケンス**アクティビティ。  
  
15. クリックして、**相互運用機能**上のアクティビティ、 **[参照] をクリックしています.** ラベルを入力**DiscountCalculator**で、**型名**ボックスし、をクリックして**OK**です。  
  
    > [!NOTE]
    >  <xref:System.Activities.Statements.Interop> アクティビティをワークフローに追加し、`DiscountCalculator` 型を <xref:System.Activities.Statements.Interop.ActivityType%2A> として指定すると、<xref:System.Activities.Statements.Interop> アクティビティは 3 つの <xref:System.Activities.ArgumentDirection.In> 引数と 3 つの <xref:System.Activities.ArgumentDirection.Out> 引数を公開します。これは `DiscountCalculator` アクティビティの 3 つのパブリック プロパティを表します。 <xref:System.Activities.ArgumentDirection.In>引数は、3 つのパブリック プロパティと、3 つと同じ名前を付ける<xref:System.Activities.ArgumentDirection.Out>引数と一致する名前がある**アウト**プロパティ名に付加します。 次の手順では、前の手順で作成したワークフロー引数を、<xref:System.Activities.Statements.Interop> アクティビティの引数にバインドします。  
  
16. 型`DiscountPercent`に、 **VB の式を入力**の右側のボックスに、 **DiscountPercentOut**プロパティと TAB キーを押します。  
  
17. 型`Subtotal`に、 **VB の式を入力**の右側のボックスに、 **Subtotal**プロパティと TAB キーを押します。  
  
18. 型`Total`に、 **VB の式を入力**の右側のボックスに、 **TotalOut**プロパティと TAB キーを押します。  
  
19. 右クリック**Program.cs**で**ソリューション エクスプ ローラー**選択**コードの表示**です。  
  
20. ファイルの先頭に次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. `CalculateDiscountInCode` メソッドに含まれる `Main` メソッドの呼び出しをコメント アウトし、次のコードを追加します。  
  
    > [!NOTE]
    >  前の手順を実行せず、既定の `Main` コードのままの場合、`Main` の内容を次のコードに置き換えます。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. 次のコードを含む `Program` と呼ばれる `CalculateDiscountUsingDesignerWorkflow` クラスで新しいメソッドを作成します。  
  
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
  
23. Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。 異なる `Subtotal` の額を指定するには、次のコードの `SubtotalValue` 値を変更します。  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>ルール機能の概要  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] ルール エンジンは、フォワード チェーンをサポートする優先順位に基づく方法で、ルールの処理をサポートしています。 単一のアイテムまたはコレクション内のアイテムについて、ルールを評価できます。 ルールの概要および特定のルール機能に関する情報については、次の表を参照してください。  
  
|ルール機能|ドキュメント|  
|-------------------|-------------------|  
|ルールの概要|[Windows Workflow Foundation ルール エンジンの概要](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|RuleSet|[ワークフローでの RuleSets の使用](http://go.microsoft.com/fwlink/?LinkId=178516)と <xref:System.Workflow.Activities.Rules.RuleSet>|  
|ルールの評価|[RuleSets 内のルールの評価](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|ルール チェーン|[フォワード チェーン コントロール](http://go.microsoft.com/fwlink/?LinkId=178518)と[ルールのフォワード チェーン](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|ルール内コレクションの処理|[ルール内コレクションの処理](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|PolicyActivity の使用|[PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink/?LinkId=178521)と <xref:System.Workflow.Activities.PolicyActivity>|  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] で作成したワークフローでは、たとえば宣言的アクティビティ条件や条件付きアクティビティ ([!INCLUDE[wf1](../../../includes/wf1-md.md)]、<xref:System.Workflow.Activities.ConditionedActivityGroup> など) など、<xref:System.Workflow.Activities.ReplicatorActivity> に用意されているルール機能のすべてを使用するわけではありません。 必要に応じて、この機能は [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] および [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を使用して作成したワークフローに使用できます。 詳細については、次を参照してください。[移行ガイダンス](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)です。
