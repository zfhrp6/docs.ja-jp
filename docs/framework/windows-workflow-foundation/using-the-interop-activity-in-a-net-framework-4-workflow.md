---
title: ".NET Framework 4 ワークフローでの相互運用アクティビティの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# .NET Framework 4 ワークフローでの相互運用アクティビティの使用
使用して作成されたアクティビティ [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] または [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] で使用できる、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を使用してワークフロー、 <xref:System.Activities.Statements.Interop> アクティビティ。 このトピックの概要を使用して、 <xref:System.Activities.Statements.Interop> アクティビティ。  
  
> [!NOTE]
>   <xref:System.Activities.Statements.Interop> ワークフローのプロジェクトで、アクティビティがワークフロー デザイナー ツールボックスに表示されない、 **ターゲット フレームワーク** ] に設定 **.Net Framework 4** またはそれ以降。  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>.NET Framework 4.5 ワークフローでの相互運用アクティビティの使用  
 このトピックでは、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティを含む `DiscountCalculator` アクティビティ ライブラリを作成します。  `DiscountCalculator` 購入額に基づいて割引を計算してから構成され、 <xref:System.Workflow.Activities.SequenceActivity> を含む、 <xref:System.Workflow.Activities.PolicyActivity>します。  
  
> [!NOTE]
>   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] このトピックで作成したアクティビティを使用して、 <xref:System.Workflow.Activities.PolicyActivity> アクティビティのロジックを実装します。 カスタムを使用する必要はありません [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] アクティビティまたは <xref:System.Activities.Statements.Interop> でルールを使用するためにアクティビティ、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフローです。 ルールを使用する例については、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフローを使用せず、 <xref:System.Activities.Statements.Interop> アクティビティを参照してください、 [.NET Framework 4.5 のポリシー アクティビティ](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) サンプルです。  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>.NET Framework 3.5 アクティビティ ライブラリ プロジェクトを作成するには  
  
1.  開いている [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 選択 **新規** し **プロジェクト.**  **ファイル** メニュー。  
  
2.  展開、 **その他のプロジェクトの種類** 内のノード、 **インストールされたテンプレート** ペイン **Visual Studio ソリューション**します。  
  
3.  選択 **空のソリューション** から、 **Visual Studio ソリューション** ] ボックスの一覧です。 型 `PolicyInteropDemo` で、 **名前** ボックスし、をクリックして **OK**します。  
  
4.  右クリック **PolicyInteropDemo** で **ソリューション エクスプ ローラー** 選択 **追加** し **新しいプロジェクト]**します。  
  
    > [!TIP]
    >  場合、 **ソリューション エクスプ ローラー** ウィンドウが表示されている、選択ができない **ソリューション エクスプ ローラー** から、 **ビュー** メニュー。  
  
5.   **インストールされたテンプレート** 一覧で、[ **Visual c#** し **ワークフロー**します。 選択 **.NET Framework 3.5** クリックして .NET Framework のバージョンのドロップダウン リストから **ワークフロー アクティビティ ライブラリ** から、 **テンプレート** ] ボックスの一覧です。  
  
6.  型 `PolicyActivityLibrary` で、 **名前** ボックスし、をクリックして **OK**します。  
  
7.  右クリック **Activity1.cs** で **ソリューション エクスプ ローラー** 選択 **削除**します。 **[OK]** をクリックして確定します。  
  
#### <a name="to-create-the-discountcalculator-activity"></a>DiscountCalculator アクティビティを作成するには  
  
1.  右クリック **PolicyActivityLibrary** で **ソリューション エクスプ ローラー** 選択 **追加** し **アクティビティ]**します。  
  
2.  選択 **アクティビティ (コード分離付き)** から、 **Visual c# アイテム** ] ボックスの一覧です。 型 `DiscountCalculator` で、 **名前** ボックスし、をクリックして **OK**します。  
  
3.  右クリック **DiscountCalculator.xoml** で **ソリューション エクスプ ローラー** 選択 **コードの表示**します。  
  
4.  `DiscountCalculator` クラスに次の 3 つのプロパティを追加します。  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  右クリック **DiscountCalculator.xoml** で **ソリューション エクスプ ローラー** 選択 **ビュー デザイナー**します。  
  
6.  ドラッグ、 **ポリシー** からアクティビティ、 **Windows Workflow v3.0** のセクションで、 **ツールボックス** にドロップし、 **DiscountCalculator** アクティビティ。  
  
    > [!TIP]
    >  場合、 **ツールボックス** ウィンドウが表示されている、選択ができない **ツールボックス** から、 **ビュー** メニュー。  
  
#### <a name="to-configure-the-rules"></a>ルールを構成するには  
  
1.  新しく追加された] をクリックして **ポリシー** アクティビティをまだ選択されていない場合にオンにします。  
  
2.  クリックして、 **RuleSetReference** プロパティに、 **プロパティ** ウィンドウを選択し、プロパティの右側にある省略記号ボタンをクリックします。  
  
    > [!TIP]
    >  場合、 **プロパティ** ウィンドウが表示されていない、選択 **プロパティ] ウィンドウ** から、 **ビュー** メニュー。  
  
3.  選択 **... [新規**します。  
  
4.  クリックして **ルールの追加**します。  
  
5.  次の式を入力、 **条件** ボックス。  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  次の式を入力、 **Then アクション** ボックス。  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  クリックして **ルールの追加**します。  
  
8.  次の式を入力、 **条件** ボックス。  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. 次の式を入力、 **Then アクション** ボックス。  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. クリックして **ルールの追加**します。  
  
11. 次の式を入力、 **条件** ボックス。  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. 次の式を入力、 **Then アクション** ボックス。  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. 次の式を入力、 **Else アクション** ボックス。  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. をクリックして **OK** を閉じる、 **ルール セット エディター** ] ダイアログ ボックス。  
  
15. 新たに作成されたことを確認 <xref:System.Workflow.Activities.Rules.RuleSet> で選択した、 **名前** 一覧を開き、をクリックして **OK**します。  
  
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
  
 ときに、 <xref:System.Workflow.Activities.PolicyActivity> 実行されると、これらの 3 つのルールが評価および変更、 `Subtotal`, 、`DiscountPercent`, と `Total` プロパティの値を `DiscountCalculator` を目的の割引を計算するアクティビティ。  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>DiscountCalculator アクティビティと相互運用アクティビティの使用  
 使用する、 `DiscountCalculator` 内のアクティビティ、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 、ワークフロー、 <xref:System.Activities.Statements.Interop> アクティビティを使用します。 このセクションの 2 つのワークフローが作成され、一方を使用する方法を示しているコードとワークフロー デザイナーを使用して 1 つを使用して、 <xref:System.Activities.Statements.Interop> アクティビティと、 `DiscountCalculator` アクティビティ。 両方のワークフローに同じホスト アプリケーションを使用します。  
  
#### <a name="to-create-the-host-application"></a>ホスト アプリケーションを作成するには  
  
1.  右クリック **PolicyInteropDemo** で **ソリューション エクスプ ローラー** 選択 **追加**, 、し **新しいプロジェクト]**します。  
  
2.  いることを確認 **.NET Framework 4.5** .NET Framework のバージョンのドロップダウン リストで選択され、選択  **ワークフロー コンソール アプリケーション** から、 **Visual c# アイテム** ] ボックスの一覧です。  
  
3.  型 `PolicyInteropHost` に、 **名前** ボックスし、をクリックして **OK**します。  
  
4.  右クリック **PolicyInteropHost** で **ソリューション エクスプ ローラー** 選択 **プロパティ**します。  
  
5.   **ターゲット フレームワーク** ドロップ ダウン ボックスの一覧で、選択した項目を変更する **.NET Framework 4 Client Profile** に **.NET Framework 4.5**します。 クリックして **はい** を確認します。  
  
6.  右クリック **PolicyInteropHost** で **ソリューション エクスプ ローラー** 選択 **参照の追加]**します。  
  
7.  選択 **PolicyActivityLibrary** から、 **プロジェクト** ] タブでをクリックし、 **OK**します。  
  
8.  右クリック **PolicyInteropHost** で **ソリューション エクスプ ローラー** 選択 **参照の追加]**します。  
  
9. 選択 **System.Workflow.Activities**, 、**System.Workflow.ComponentModel**, 、し **System.Workflow.Runtime** から、 **.NET** ] タブでをクリックし、 **OK**します。  
  
10. 右クリック **PolicyInteropHost** で **ソリューション エクスプ ローラー** 選択 **スタートアップ プロジェクトとして設定**します。  
  
11. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
### <a name="using-the-interop-activity-in-code"></a>コードでの Interop アクティビティの使用  
 含むコードを使用して、ワークフロー定義を作成この例では、 <xref:System.Activities.Statements.Interop> アクティビティおよび `DiscountCalculator` アクティビティ。 使用して、このワークフローが呼び出される <xref:System.Activities.WorkflowInvoker> を使用してコンソールに、ルールの評価結果が書き込まれると、 <xref:System.Activities.Statements.WriteLine> アクティビティ。  
  
##### <a name="to-use-the-interop-activity-in-code"></a>コードで Interop アクティビティを使用するには  
  
1.  右クリック **Program.cs** で **ソリューション エクスプ ローラー** 選択 **コードの表示**します。  
  
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
    >   `Subtotal`, 、`DiscountPercent`, 、および `Total` のプロパティ、 `DiscountCalculator` の引数として表示、 <xref:System.Activities.Statements.Interop> アクティビティ、およびローカル ワークフロー変数にバインドで、 <xref:System.Activities.Statements.Interop> アクティビティの <xref:System.Activities.Statements.Interop.ActivityProperties%2A> コレクションです。 `Subtotal` として追加、 <xref:System.Activities.ArgumentDirection> 引数のため、 `Subtotal` にデータが流れる、 <xref:System.Activities.Statements.Interop> アクティビティ、および `DiscountPercent` と `Total` として追加されます <xref:System.Activities.ArgumentDirection> 引数のデータであるので、 <xref:System.Activities.Statements.Interop> アクティビティ。 注意してください、2 つ <xref:System.Activities.ArgumentDirection> 引数はという名前で追加 `DiscountPercentOut` と `TotalOut` を表すことを示す <xref:System.Activities.ArgumentDirection> 引数。  `DiscountCalculator` として型が指定されている、 <xref:System.Activities.Statements.Interop> アクティビティの <xref:System.Activities.Statements.Interop.ActivityType%2A>します。  
  
5.  Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。 `Subtotal` 値を異なる値に置き換え、`DiscountCalculator` アクティビティに用意されているさまざまな割引レベルをテストします。  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>ワークフロー デザイナーでの Interop アクティビティの使用  
 この例では、ワークフロー デザイナーを使用してワークフローを作成します。 このワークフローには、前の例と同じ機能を除くよりも使用する代わりに、 <xref:System.Activities.Statements.WriteLine> 、割引を表示するアクティビティ ホスト アプリケーションを取得し、ワークフローの完了時に割引情報が表示されます。 また、データを含むローカル ワークフロー変数を使用するのではなく、ワークフローの呼び出し時に、引数がワークフロー デザイナーで作成され、値はホストから渡されます。  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>ワークフロー デザイナーで作成したワークフローを使用して PolicyActivity をホストするには  
  
1.  右クリック **Workflow1.xaml** で **ソリューション エクスプ ローラー** 選択 **削除**します。 **[OK]** をクリックして確定します。  
  
2.  右クリック **PolicyInteropHost** で **ソリューション エクスプ ローラー** 選択 **追加**, 、**新しい項目]**します。  
  
3.  展開、 **Visual c# アイテム** ノード **ワークフロー**します。 選択 **アクティビティ** から、 **Visual c# アイテム** ] ボックスの一覧です。  
  
4.  型 `DiscountWorkflow` に、 **名前** ボックスし、をクリックして **追加**します。  
  
5.  クリックして、 **引数** を表示するワークフロー デザイナーの左下のボタン、 **引数** ウィンドウです。  
  
6.  クリックして **引数の作成**します。  
  
7.  型 `Subtotal` に、 **名前** ボックスで、 **で** から、 **方向** ドロップダウン リストで、[ **二重** から、 **引数の型** ドロップ ダウンし、enter キーを押して引数を保存します。  
  
    > [!NOTE]
    >  場合 **二重** に含まれていない、 **引数の型** ドロップダウン リストで、 **の種類の [参照]**, 、型 `System.Double` で、 **型名** ボックスし、をクリックして **[ok]**します。  
  
8.  クリックして **引数の作成**します。  
  
9. 型 `DiscountPercent` に、 **名前** ボックスで、 **アウト** から、 **方向** ドロップダウン リストで、[ **二重** から、 **引数の型** ドロップ ダウンし、enter キーを押して引数を保存します。  
  
10. クリックして **引数の作成**します。  
  
11. 型 `Total` に、 **名前** ボックスで、 **アウト** から、 **方向** ドロップダウン リストで、[ **二重** から、 **引数の型** ドロップ ダウンし、enter キーを押して引数を保存します。  
  
12. クリックして、 **引数** を閉じる、ワークフロー デザイナーの左下のボタン、 **引数** ウィンドウです。  
  
13. ドラッグ、 **シーケンス** からアクティビティ、 **制御フロー** のセクションで、 **ツールボックス** し、ワークフロー デザイナー画面にドロップします。  
  
14. ドラッグ、 **相互運用機能** からアクティビティ、 **移行** のセクションで、 **ツールボックス** にドロップし、 **シーケンス** アクティビティ。  
  
15. クリックして、 **相互運用機能** 上のアクティビティ、 **を参照する] をクリックします.** ラベルを入力 **DiscountCalculator** で、 **型名** ボックスし、をクリックして **OK**します。  
  
    > [!NOTE]
    >  ときに、 <xref:System.Activities.Statements.Interop> アクティビティがワークフローに追加された、 `DiscountCalculator` として型を指定の <xref:System.Activities.Statements.Interop.ActivityType%2A>, 、 <xref:System.Activities.Statements.Interop> アクティビティでは、3 つによって公開される <xref:System.Activities.ArgumentDirection> 引数と 3 つ <xref:System.Activities.ArgumentDirection> の 3 つのパブリック プロパティを表す引数、 `DiscountCalculator` アクティビティ。  <xref:System.Activities.ArgumentDirection> 引数が 3 つのパブリック プロパティと、3 つと同じ名前を付ける <xref:System.Activities.ArgumentDirection> 引数と同じ名前を持つ **アウト** プロパティ名に付加します。 次の手順では、前の手順で作成したワークフロー引数がバインドされて、 <xref:System.Activities.Statements.Interop> アクティビティの引数。  
  
16. 型 `DiscountPercent` に、 **VB の式を入力して** の右側のボックスに、 **DiscountPercentOut** プロパティと TAB キーを押します。  
  
17. 型 `Subtotal` に、 **VB の式を入力して** の右側のボックスに、 **Subtotal** プロパティと TAB キーを押します。  
  
18. 型 `Total` に、 **VB の式を入力して** の右側のボックスに、 **TotalOut** プロパティと TAB キーを押します。  
  
19. 右クリック **Program.cs** で **ソリューション エクスプ ローラー** 選択 **コードの表示**します。  
  
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
|RuleSet|[ワークフロー内での RuleSets の使用](http://go.microsoft.com/fwlink/?LinkId=178516) と <xref:System.Workflow.Activities.Rules.RuleSet>|  
|ルールの評価|[RuleSets 内のルールの評価](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|ルール チェーン|[フォワード チェーン コントロール](http://go.microsoft.com/fwlink/?LinkId=178518) と [ルールのフォワード チェーン](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|ルール内コレクションの処理|[ルール内コレクションの処理](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|PolicyActivity の使用|[PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink/?LinkId=178521) と <xref:System.Workflow.Activities.PolicyActivity>|  
  
 作成されたワークフロー [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] によって提供されるルール機能の一部しか使用しない [!INCLUDE[wf1](../../../includes/wf1-md.md)], 、宣言的アクティビティ条件やなどの条件付きアクティビティなど、 <xref:System.Workflow.Activities.ConditionedActivityGroup> と <xref:System.Workflow.Activities.ReplicatorActivity>します。 必要に応じて、この機能は [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] および [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を使用して作成したワークフローに使用できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][移行ガイダンス](../../../docs/framework/windows-workflow-foundation//migration-guidance.md)します。