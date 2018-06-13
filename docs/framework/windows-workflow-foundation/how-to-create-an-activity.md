---
title: アクティビティを作成する方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 18b03468646a4d016e383f5662d9827551d1141c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519608"
---
# <a name="how-to-create-an-activity"></a>アクティビティを作成する方法
アクティビティは [!INCLUDE[wf1](../../../includes/wf1-md.md)] の動作の中心的な単位です。 アクティビティの実行ロジックはマネージ コードで実装できます。または他のアクティビティを使用して実装できます。 このトピックでは、2 つのアクティビティを作成する方法について説明します。 最初のアクティビティは、コードを使用してその実行ロジックを実装する単純なアクティビティです。 2 番目のアクティビティの実装は他のアクティビティを使用して定義されています。 これらのアクティビティは、チュートリアルの次の手順で使用します。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### <a name="to-create-the-activity-library-project"></a>アクティビティ ライブラリ プロジェクトを作成するには  
  
1.  開いている[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選択**新規**、**プロジェクト**から、**ファイル**メニュー。  
  
2.  展開、**その他のプロジェクトの種類**内のノード、**インストール済み**、**テンプレート**選択**Visual Studio ソリューション**です。  
  
3.  選択**空のソリューション**から、 **Visual Studio ソリューション** ボックスの一覧です。 .NET Framework バージョンのドロップダウン リストで **[.NET Framework 4.5]** が選択されていることを確認します。 型`WF45GettingStartedTutorial`で、**名前**ボックスし、をクリックして**OK**です。  
  
4.  右クリック**WF45GettingStartedTutorial**で**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**です。  
  
    > [!TIP]
    >  **ソリューション エクスプローラー** ウィンドウが表示されない場合は、 **[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。  
  
5.  **[インストール済み]** ノードで、 **[Visual C#]**、 **[ワークフロー]** (または **[Visual Basic]**、 **[ワークフロー]**) の順に選択します。 いることを確認 **.NET Framework 4.5**でが選択されている、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]バージョンのドロップダウン リスト。 選択**アクティビティ ライブラリ**から、**ワークフロー**  ボックスの一覧です。 型`NumberGuessWorkflowActivities`で、**名前**ボックスし、をクリックして**OK**です。  
  
    > [!NOTE]
    >  Visual Studio で第一言語として設定されているプログラミング言語に応じて、 **[インストール済み]** ノードの **[他の言語]** ノードの下に、 **[Visual C#]** ノードまたは **[Visual Basic]** ノードが表示されます。  
  
6.  右クリック**Activity1.xaml**で**ソリューション エクスプ ローラー**選択**削除**です。 **[OK]** をクリックして確定します。  
  
### <a name="to-create-the-readint-activity"></a>ReadInt アクティビティを作成するには  
  
1.  選択**新しい項目の追加**から、**プロジェクト**メニュー。  
  
2.  **インストール**、**共通項目**ノードで、選択**ワークフロー**です。 選択**コード アクティビティ**から、**ワークフロー**  ボックスの一覧です。  
  
3.  型`ReadInt`に、**名前**ボックスし、をクリックして**追加**です。  
  
4.  既存の `ReadInt` 定義を次の定義に置き換えます。  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` アクティビティは、コード アクティビティ テンプレートの既定値である <xref:System.Activities.NativeActivity%601> ではなく <xref:System.Activities.CodeActivity> から派生します。 <xref:System.Activities.CodeActivity%601> は、<xref:System.Activities.Activity%601.Result%2A> 引数を介して公開される 1 つの結果がアクティビティによって提供される場合に使用できますが、<xref:System.Activities.CodeActivity%601> ではブックマークの使用がサポートされていないため、<xref:System.Activities.NativeActivity%601> が使用されます。  
  
### <a name="to-create-the-prompt-activity"></a>Prompt アクティビティを作成するには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。 プロジェクトをビルドすると、このプロジェクトの `ReadInt` アクティビティを使用して、この手順からカスタム アクティビティをビルドできます。  
  
2.  選択**新しい項目の追加**から、**プロジェクト**メニュー。  
  
3.  **インストール**、**共通項目**ノードで、選択**ワークフロー**です。 選択**アクティビティ**から、**ワークフロー**  ボックスの一覧です。  
  
4.  型`Prompt`に、**名前**ボックスし、をクリックして**追加**です。  
  
5.  ダブルクリックして**Prompt.xaml**で**ソリューション エクスプ ローラー**をまだ表示されていない場合、デザイナーで表示します。  
  
6.  をクリックして**引数**を表示するアクティビティ デザイナーの左下横で、**引数**ウィンドウです。  
  
7.  をクリックして**引数の作成**です。  
  
8.  型`BookmarkName`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**文字列**から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。  
  
9. をクリックして**引数の作成**です。  
  
10. 型`Result`に、**名前**、新たに追加の下にあるボックスを`BookmarkName`引数で、**アウト**から、**方向**ドロップダウン リストで、**Int32**から、**引数の型**ドロップダウン リストとし、ENTER キーを押します。  
  
11. をクリックして**引数の作成**です。  
  
12. 型`Text`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、**文字列**から**引数の型**ドロップダウン リストと、引数を保存するには ENTER キーを押します。  
  
     これら 3 つの引数は、次の手順で、<xref:System.Activities.Statements.WriteLine> アクティビティに追加される `ReadInt` アクティビティと `Prompt` アクティビティの対応する引数にバインドされます。  
  
13. をクリックして**引数**を閉じる、アクティビティ デザイナーの左下横で、**引数**ウィンドウです。  
  
14. ドラッグ、**シーケンス**からアクティビティを**制御フロー**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**のラベル、**プロンプト**アクティビティ デザイナー。  
  
    > [!TIP]
    >  場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。  
  
15. ドラッグ、 **WriteLine**からアクティビティを**プリミティブ**のセクションで、**ツールボックス**上にドロップし、**ここにアクティビティをドロップ**のラベル、**シーケンス**アクティビティ。  
  
16. バインド、**テキスト**の引数、 **WriteLine**アクティビティを**テキスト**の引数、**プロンプト**」と入力してアクティビティ`Text`**c# 式を入力**または**VB の式を入力**ボックスに、**プロパティ**キー 2 回のウィンドウとし、TAB キーを押します。 これで、IntelliSense リスト メンバー ウィンドウを閉じ、プロパティから選択を外してプロパティ値を保存します。 このプロパティは、」と入力して設定することもできます`Text`に、 **c# 式を入力**または**VB の式を入力**アクティビティ自体のボックスです。  
  
    > [!TIP]
    >  場合、**プロパティ ウィンドウ**が表示されていない select**プロパティ ウィンドウ**から、**ビュー**メニュー。  
  
17. ドラッグ、 **ReadInt**からアクティビティを**NumberGuessWorkflowActivities**のセクションで、**ツールボックス**内にドロップし、**シーケンス**アクティビティの後になるように、 **WriteLine**アクティビティ。  
  
18. バインド、 **BookmarkName**の引数、 **ReadInt**アクティビティを**BookmarkName**の引数、**プロンプト** 」と入力してアクティビティ`BookmarkName`に、 **VB の式を入力**の右側のボックスに、 **BookmarkName**の引数、**プロパティ ウィンドウ**、TAB キーを押します 2IntelliSense リスト メンバー ウィンドウを閉じて、プロパティを保存する時間します。  
  
19. バインド、**結果**の引数、 **ReadInt**アクティビティを**結果**の引数、**プロンプト**」と入力してアクティビティ`Result`**VB の式を入力**の右側のボックスに、**結果**の引数、**プロパティ ウィンドウ**とし、TAB キーを 2 回押します。  
  
20. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     これらのアクティビティを使用してワークフローを作成する方法については、チュートリアルでは、次の手順を参照してください[する方法: ワークフローを作成](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [カスタム アクティビティの設計と実装](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [カスタム アクティビティ デザイナーでの ExpressionTextBox の使用](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
