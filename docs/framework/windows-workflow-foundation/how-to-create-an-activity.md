---
title: "アクティビティを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: 39
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 39
---
# アクティビティを作成する方法
アクティビティは [!INCLUDE[wf1](../../../includes/wf1-md.md)] の動作の中心的な単位です。アクティビティの実行ロジックはマネージ コードで実装できます。または他のアクティビティを使用して実装できます。このトピックでは、2 つのアクティビティを作成する方法について説明します。最初のアクティビティは、コードを使用してその実行ロジックを実装する単純なアクティビティです。2 番目のアクティビティの実装は他のアクティビティを使用して定義されています。これらのアクティビティは、チュートリアルの次の手順で使用します。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「[Windows Workflow Foundation \(WF45\) \- チュートリアル入門](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### アクティビティ ライブラリ プロジェクトを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を開き、**\[ファイル\]** メニューの **\[新規作成\]** の **\[プロジェクト\]** をクリックします。  
  
2.  **\[インストールされているテンプレート\]** の一覧で **\[その他のプロジェクトの種類\]** ノードを展開し、**\[Visual Studio ソリューション\]** を選択します。  
  
3.  **\[Visual Studio ソリューション\]** リストで **\[空のソリューション\]** を選択します。.NET Framework バージョンのドロップダウン リストで **\[.NET Framework 4.5\]** が選択されていることを確認します。**\[名前\]** ボックスに「`WF45GettingStartedTutorial`」と入力し、**\[OK\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で **WF45GettingStartedTutorial** を右クリックし、**\[追加\]** をポイントして、**\[新しいプロジェクト\]** をクリックします。  
  
    > [!TIP]
    >  **ソリューション エクスプローラー** ウィンドウが表示されない場合は、**\[表示\]** メニューの **\[ソリューション エクスプローラー\]** をクリックします。  
  
5.  **\[インストール済み\]** ノードで、**\[Visual C\#\]**、**\[ワークフロー\]** \(または **\[Visual Basic\]**、**\[ワークフロー\]**\) の順に選択します。[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] バージョンのドロップダウン リストで **\[.NET Framework 4.5\]** が選択されていることを確認します。**\[ワークフロー\]** リストで **\[アクティビティ ライブラリ\]** を選択します。**\[名前\]** ボックスに「`NumberGuessWorkflowActivities`」と入力し、**\[OK\]** をクリックします。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で第一言語として設定されているプログラミング言語に応じて、**\[インストール済み\]** ノードの **\[他の言語\]** ノードの下に、**\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードが表示されます。  
  
6.  **ソリューション エクスプローラー**で **Activity1.xaml** を右クリックし、**\[削除\]** をクリックします。**\[OK\]** をクリックして確定します。  
  
### ReadInt アクティビティを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[インストール済み\]** の **\[共通項目\]** ノードで、**\[ワークフロー\]** を選択します。**\[ワークフロー\]** リストで **\[コード アクティビティ\]** を選択します。  
  
3.  **\[名前\]** ボックスに「`ReadInt`」と入力し、**\[追加\]** をクリックします。  
  
4.  既存の `ReadInt` 定義を次の定義に置き換えます。  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` アクティビティは、コード アクティビティ テンプレートの既定値である <xref:System.Activities.CodeActivity> ではなく <xref:System.Activities.NativeActivity%601> から派生します。<xref:System.Activities.CodeActivity%601> は、<xref:System.Activities.Activity%601.Result%2A> 引数を介して公開される 1 つの結果がアクティビティによって提供される場合に使用できますが、<xref:System.Activities.CodeActivity%601> ではブックマークの使用がサポートされていないため、<xref:System.Activities.NativeActivity%601> が使用されます。  
  
### Prompt アクティビティを作成するには  
  
1.  **Ctrl** キーと **Shift** キーを押しながら **B** キーを押して、プロジェクトをビルドします。プロジェクトをビルドすると、このプロジェクトの `ReadInt` アクティビティを使用して、この手順からカスタム アクティビティをビルドできます。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[インストール済み\]** の **\[共通項目\]** ノードで、**\[ワークフロー\]** を選択します。**\[ワークフロー\]** リストで **\[アクティビティ\]** を選択します。  
  
4.  **\[名前\]** ボックスに「`Prompt`」と入力し、**\[追加\]** をクリックします。  
  
5.  **ソリューション エクスプローラー**で **Prompt.xaml** をダブルクリックし、デザイナーにワークフローを表示します \(まだ表示されていない場合\)。  
  
6.  アクティビティ デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを表示します。  
  
7.  **\[引数の作成\]** をクリックします。  
  
8.  **\[名前\]** ボックスに「`BookmarkName`」と入力し、**\[方向\]** ボックスの一覧の **\[IN\]** を選択して、**\[引数の型\]** ボックスの一覧の **\[String\]** を選択し、Enter キーを押して引数を保存します。  
  
9. **\[引数の作成\]** をクリックします。  
  
10. 新しく追加した `BookmarkName` 引数の下にある **\[名前\]** ボックスに「`Result`」と入力し、**\[方向\]** ボックスで **\[OUT\]** を選択して、**\[引数の型\]** ドロップダウン リストで **\[Int32\]** を選択し、Enter キーを押します。  
  
11. **\[引数の作成\]** をクリックします。  
  
12. **\[名前\]** ボックスに「`Text`」と入力し、**\[方向\]** ボックスで **\[IN\]** を選択して、**\[引数の型\]** ボックスで **\[String\]** を選択し、Enter キーを押して引数を保存します。  
  
     これら 3 つの引数は、次の手順で、`Prompt` アクティビティに追加される <xref:System.Activities.Statements.WriteLine> アクティビティと `ReadInt` アクティビティの対応する引数にバインドされます。  
  
13. アクティビティ デザイナーの左下にある **\[引数\]** をクリックし、**\[引数\]** ペインを閉じます。  
  
14. **ツールボックス**の **\[制御フロー\]** セクションから **Sequence** アクティビティをドラッグし、**Prompt** アクティビティ デザイナーの **\[ここにアクティビティをドロップ\]** ラベルの上にドロップします。  
  
    > [!TIP]
    >  **\[ツールボックス\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[ツールボックス\]** をクリックします。  
  
15. **ツールボックス**の **\[プリミティブ\]** セクションから **WriteLine** アクティビティをドラッグし、**Sequence** アクティビティの **\[ここにアクティビティをドロップ\]** ラベルの上にドロップします。  
  
16. **\[プロパティ\]** ウィンドウの **\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに「`Text`」と入力して、**WriteLine** アクティビティの **Text** 引数を **Prompt** アクティビティの **Text** 引数にバインドします。次に Tab キーを 2 回押します。これで、IntelliSense リスト メンバー ウィンドウを閉じ、プロパティから選択を外してプロパティ値を保存します。このプロパティは、アクティビティ自体の **\[C\# の式を入力してください\]** ボックスまたは **\[VB の式を入力してください\]** ボックスに「`Text`」と入力して設定することもできます。  
  
    > [!TIP]
    >  **\[プロパティ\]** ウィンドウが表示されていない場合は、**\[表示\]** メニューの **\[プロパティ ウィンドウ\]** を選択します。  
  
17. **ツールボックス**の **\[NumberGuessWorkflowActivities\]** セクションから **ReadInt** アクティビティをドラッグし、**WriteLine** アクティビティの後になるように **Sequence** アクティビティ内にドロップします。  
  
18. **\[プロパティ\]** ウィンドウで **BookmarkName** 引数の右にある **\[VB の式を入力してください\]** ボックスに「`BookmarkName`」と入力して、**ReadInt** アクティビティの **BookmarkName** 引数を **Prompt** アクティビティの **BookmarkName** 引数にバインドします。次に Tab キーを 2 回押して IntelliSense リスト メンバー ウィンドウを閉じ、プロパティを保存します。  
  
19. **\[プロパティ\]** ウィンドウの **Result** 引数の右にある **\[VB の式を入力してください\]** ボックスに「`Result`」と入力して、**ReadInt** アクティビティの **Result** 引数を **Prompt** アクティビティの **Result** 引数にバインドします。次に Tab キーを 2 回押します。  
  
20. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     これらのアクティビティを使用してワークフローを作成する手順については、チュートリアルの次の手順「[ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)」を参照してください。  
  
## 参照  
 <xref:System.Activities.CodeActivity>   
 <xref:System.Activities.NativeActivity%601>   
 [カスタム アクティビティの設計と実装](../../../docs/framework/windows-workflow-foundation//designing-and-implementing-custom-activities.md)   
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)   
 [カスタム アクティビティ デザイナーでの ExpressionTextBox の使用](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)