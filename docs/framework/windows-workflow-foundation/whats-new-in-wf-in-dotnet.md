---
title: どのような&#39;.NET 4.5 での Windows Workflow Foundation の新機能として s
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4aa77a0135cea18847c4d4425171b0bdcf447988
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="what39s-new-in-windows-workflow-foundation-in-net-45"></a>どのような&#39;.NET 4.5 での Windows Workflow Foundation の新機能として s
Windows Workflow Foundation (WF) で[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]新しいアクティビティ、デザイナー機能、およびワークフロー開発モデルなど、多くの新機能が導入されています。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で導入された新しいワークフロー機能の多くは、ホストを変更したワークフロー デザイナーでサポートされています (ただし、すべての機能がサポートされているわけではありません)。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] サポートされている新機能を参照してください[、再ホストされたワークフロー デザイナーで新しい Workflow Foundation 4.5 機能のサポート](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)です。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] .NET 3.0 を移行して、最新バージョンを使用する .NET 3.5 ワークフロー アプリケーションを参照してください。[移行ガイダンス](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)です。 ここでは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で導入された新しいワークフロー機能の概要について説明します。  
  
> [!WARNING]
>  導入された新しい Windows Workflow Foundation 機能[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]framework の以前のバージョンを対象とするプロジェクトでは使用できません。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とするプロジェクトの対象を以前のバージョンのフレームワークに変更すると、いくつかの問題が発生する場合があります。  
>   
>  -   C# 式は、メッセージに、デザイナーで置き換えられます**値が XAML で設定された**です。  
> -   次のエラーを含む、多くのビルド エラーが発生します。  
>   
>  **ファイルの形式は、現在のターゲット フレームワークと互換性がありません。ファイル形式を変換するにはファイルを明示的に保存してください。ファイルを保存してデザイナーを閉じて後、このエラー メッセージは表示されなくなりました。**  
  
##  <a name="BKMK_Versioning"></a> ワークフローのバージョン管理  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、新しい <xref:System.Activities.WorkflowIdentity> クラスに基づいて、いくつかの新しいバージョン管理機能が導入されました。 <xref:System.Activities.WorkflowIdentity> には、ワークフロー アプリケーションの作成者向けに、永続化されたワークフロー インスタンスをその定義でマップするメカニズムが備わっています。  
  
-   <xref:System.Activities.WorkflowApplication> ホスティングを使用する開発者は、<xref:System.Activities.WorkflowIdentity> を使用して、ワークフローの複数のバージョンを同時にホストできます。 永続化されたワークフロー インスタンスは新しい <xref:System.Activities.WorkflowApplicationInstance> クラスを使用して読み込むことができ、ホストは <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> を使用して、<xref:System.Activities.WorkflowApplication> のインスタンス化時に適切なバージョンのワークフロー定義を提供できます。 詳細については、次を参照してください。[を使用して WorkflowIdentity と Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md)と[する方法: 複数のバージョンのホストはワークフロー サイド バイ サイドの](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。  
  
-   現在、<xref:System.ServiceModel.WorkflowServiceHost> は複数のバージョンのホストです。 ワークフロー サービスの新しいバージョンを配置すると、新しいインスタンスが新しいサービスを使用して作成されますが、既存のインスタンスは以前のバージョンを使用して完了します。 詳細については、次を参照してください。 [WorkflowServiceHost でサイド バイ サイドのバージョン管理](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)です。  
  
-   永続化されたワークフロー インスタンスの定義を更新するためのメカニズムを提供する動的更新が導入されました。 詳細については、次を参照してください。[動的更新](../../../docs/framework/windows-workflow-foundation/dynamic-update.md)と[する方法: を実行しているワークフロー インスタンスの定義を更新](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)です。  
  
-   SqlWorkflowInstanceStoreSchemaUpgrade.sql データベース スクリプトは、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] データベース スクリプトを使用して作成された永続性データベースを更新するために用意されています。 このスクリプトは、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] で導入された新しいバージョン管理機能をサポートするように [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 永続性データベースを更新します。 データベースで永続化されたワークフロー インスタンスは、既定のバージョン番号が付与されるため、side-by-side 実行および動的更新に参加できるようになります。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [ワークフローのバージョン管理をサポートするために .NET Framework 4 永続性データベースをアップグレードする](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)です。  
  
##  <a name="BKMK_NewActivities"></a> アクティビティ  
 組み込みのアクティビティ ライブラリには、既存のアクティビティ用の新しいアクティビティと新しい機能が含まれています。  
  
###  <a name="BKMK_NoPersistScope"></a> Nopersistscope  
 <xref:System.Activities.Statements.NoPersistScope> は、NoPersistScope の子アクティビティの実行時にワークフローが永続化されないようにする新しいコンテナー アクティビティです。 これは、ワークフローがファイル ハンドルなどのコンピューター固有のリソースを使用している場合、データベース トランザクション中など、ワークフローの永続化が適切でないシナリオで役立ちます。 以前のバージョンでは、アクティビティ実行中に永続化されないようにするために、<xref:System.Activities.NativeActivity> を使用したカスタム <xref:System.Activities.NoPersistHandle> が必要でした。  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> フローチャートの新機能  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 用に更新されたフローチャートには、次の新機能があります。  
  
-   `DisplayName` アクティビティまたは <xref:System.Activities.Statements.FlowSwitch%601> アクティビティの <xref:System.Activities.Statements.FlowDecision> プロパティは編集できます。 これにより、アクティビティ デザイナーではアクティビティの目的に関する詳細な情報を表示できます。  
  
-   フローチャートには <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A> という新しいプロパティがあります。このプロパティの既定値は `False` です。 このプロパティを `True` に設定すると、接続されていないフローチャート ノードでは検証エラーが発生します。  
  
## <a name="support-for-partial-trust"></a>部分信頼のサポート  
 [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] のワークフローでは、完全に信頼されたアプリケーション ドメインが必要でした。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、ワークフローを部分信頼環境で動作させることができます。 部分信頼環境では、サード パーティのコンポーネントは、ホストのリソースに対するフル アクセスを許可しなくても使用できます。 部分信頼でのワークフローの実行に関する問題は次のとおりです。  
  
1.  部分信頼環境では、<xref:System.Activities.Statements.Interop> アクティビティに含まれるレガシ コンポーネント (規則など) を使用することはできません。  
  
2.  <xref:System.ServiceModel.WorkflowServiceHost> において部分信頼でワークフローを実行することはできません。  
  
3.  部分信頼シナリオで例外を永続化すると、セキュリティ上の脅威になる可能性があります。 例外の永続化を無効にするには、例外が永続化されないように <xref:System.Activities.ExceptionPersistenceExtension> 型の拡張機能をプロジェクトに追加する必要があります。 この型を実装する方法を示したコード例を次に示します。  
  
    ```  
    public class ExceptionPersistenceExtension   
    {  
        public ExceptionPersistenceExtension()   
        {   
            this.PersistExceptions = false;   
        }   
        public bool PersistExceptions { get; set; }   
    }  
    ```  
  
     例外がシリアル化されない場合は、例外が <xref:System.Activities.Statements.NoPersistScope> 内で使用されていることを確認してください。  
  
4.  アクティビティの作成者は、<xref:System.Activities.Activity.CacheMetadata%2A> をオーバーライドして、ワークフロー ランタイムが型に対してリフレクションを自動的に実行しないようにする必要があります。 引数と子アクティビティには null 以外を指定する必要があり、<xref:System.Activities.ActivityMetadata.Bind%2A> は明示的に呼び出す必要があります。 オーバーライドの詳細については<xref:System.Activities.Activity.CacheMetadata%2A>を参照してください[CacheMetadata を使用してデータを公開する](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md)です。 ある型の引数のインスタンスも、`internal`または**プライベート**で明示的に作成する必要があります<xref:System.Activities.Activity.CacheMetadata%2A>リフレクションによって作成されないようにします。  
  
5.  型は、シリアル化に <xref:System.Runtime.Serialization.ISerializable> または <xref:System.SerializableAttribute> を使用しません。シリアル化する型では、<xref:System.Runtime.Serialization.DataContractSerializer> をサポートする必要があります。  
  
6.  <xref:System.Activities.Expressions.LambdaValue%601> を使用する式は <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A> を必要とするため、部分信頼では動作しません。 <xref:System.Activities.Expressions.LambdaValue%601> を使用するワークフローでは、これらの式を、<xref:System.Activities.CodeActivity%601> から派生するアクティビティと置き換える必要があります。 である必要があります。  
  
7.  部分信頼では、<xref:System.Activities.XamlIntegration.TextExpressionCompiler> または Visual Basic でホストされているコンパイラを使用して式をコンパイルすることはできませんが、以前コンパイルされた式を実行することはできます。  
  
8.  使用する 1 つのアセンブリ[レベル 2 の透過性](http://aka.ms/Level2Transparency)では使用できません[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]完全な信頼でと[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]部分的な信頼でします。  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> デザイナーの新機能  
  
###  <a name="BKMK_DesignerSearch"></a> デザイナーでの検索  
 より大規模なワークフローを管理しやすくするために、キーワードでワークフローを検索できるようになりました。 この機能は Visual Studio は; で使用できるだけです。この機能では、再ホストされたデザイナーで使用できません。 利用できる検索機能には 2 種類あります。  
  
-   クイック検索、いずれかを使用して開始**Ctrl + F**または**編集**、**検索し、置換**、**クイック検索**です。  
  
-   ファイルでは、検索するかを使用して開始**Ctrl + Shift + F**または**編集**、**検索し、置換**、**ファイル内の検索**です。  
  
 置換はサポートされていません。  
  
####  <a name="BKMK_QuickFind"></a> [クイック検索]  
 ワークフロー内で検索されるキーワードは、次のデザイナー項目に一致します。  
  
-   <xref:System.Activities.Activity> オブジェクト、<xref:System.Activities.Statements.FlowNode> オブジェクト、<xref:System.Activities.Statements.State> オブジェクト、<xref:System.Activities.Statements.Transition> オブジェクト、およびその他のカスタム フロー制御項目のプロパティ。  
  
-   変数  
  
-   引数  
  
-   式  
  
 クイック検索はデザイナーの <xref:System.Activities.Presentation.Model.ModelItem> ツリーで実行されます。 クイック検索は、ワークフロー定義にインポートされた名前空間を検索しません。  
  
####  <a name="BKMK_FindInFiles"></a> ファイル内の検索します。  
 ワークフロー内で検索されるキーワードは、ワークフロー ファイルの実際のコンテンツに一致します。 検索結果は Visual Studio の検索結果ビュー ペインに表示されます。 結果の項目をダブルクリックすると、ワークフロー デザイナーで一致を含むアクティビティに移動します。  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> 変数デザイナーと引数デザイナーのコンテキスト メニュー項目を削除します。  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、変数および引数を削除できるのは、デザイナーでキーボードを使用した場合のみでした。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、コンテキスト メニューを使用して変数および引数を削除できます。  
  
 変数デザイナーと引数デザイナーのコンテキスト メニューを次のスクリーンショットに示しています。  
  
 ![変数/引数デザイナーのコンテキスト メニュー](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> シーケンスでの自動囲い込み  
 ワークフローまたは特定のコンテナー アクティビティ (<xref:System.Activities.Statements.NoPersistScope> など) には Body アクティビティを 1 つしか含めることができないため、2 つ目のアクティビティを追加するには、開発者が最初のアクティビティを削除し、<xref:System.Activities.Statements.Sequence> アクティビティを追加してから、シーケンス アクティビティに両方のアクティビティを追加する必要がありました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、デザイナー画面に 2 つ目のアクティビティを追加すると、`Sequence` アクティビティが自動的に作成され、両方のアクティビティがラップされます。  
  
 次のスクリーンショットは、`WriteLine` の `Body` 内の `NoPersistScope` アクティビティを示しています。  
  
 ![自動&#45;の格納場所を囲む](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 次のスクリーンショットは、2 つ目の `Sequence` を 1 つ目の下にドロップしたときに `Body` 内に自動的に作成された `WriteLine` アクティビティを示しています。  
  
 ![自動的に作成された sequence アクティビティ](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> パン モード  
 デザイナーで大規模なワークフロー内をより簡単に移動するには、パン モードを有効にすると、開発者は、スクロール バーを使用する必要なく、ワークフローの表示される部分をクリックおよびドラッグして移動できるようになります。 パン モードをアクティブ化するボタンは、デザイナーの右下隅にあります。  
  
 次のスクリーンショットは、ワークフロー デザイナーの右下隅にあるパン ボタンを示しています。  
  
 ![ワークフロー デザイナーで [パン] ボタン](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 マウスの中央ボタンまたは Space キーを使用して、ワークフロー デザイナーをパンすることもできます。  
  
###  <a name="BKMK_MultiSelect"></a> 複数選択  
 複数のアクティビティを同時に選択できます。これを行うには、複数のアクティビティを囲むようにドラッグするか (パン モードが無効な場合)、Ctrl キーを押したまま目的のアクティビティを 1 つずつクリックします。  
  
 選択した複数のアクティビティは、デザイナー内でドラッグ アンド ドロップすることも、コンテキスト メニューを使用して操作することもできます。  
  
###  <a name="BKMK_DocumentOutline"></a> ワークフロー項目のアウトライン表示  
 階層ワークフローを移動しやすくするため、ワークフローのコンポーネントはツリー スタイルのアウトライン表示で示されます。 アウトライン表示で、 **ドキュメント アウトライン**ビュー。 上部のメニューから、このビューを開くには**ビュー**、**その他のウィンドウ**、 **ドキュメント アウトライン**、または Ctrl W キーと u ですキーを押します。 アウトライン表示でノードをクリックすると、ワークフロー デザイナーの対応するアクティビティに移動し、アウトライン表示が更新されて、デザイナーで選択されているアクティビティが表示されます。  
  
 完了済みワークフローからの次のスクリーン ショット、[チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)シーケンシャル ワークフローにより、アウトライン表示を示しています。  
  
 ![ワークフロー デザイナーでビューをアウトライン](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> C# 式  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] より前のバージョンでは、ワークフロー内のすべての式を Visual Basic のみで記述できました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、Visual Basic の式は Visual Basic で作成されたプロジェクトでのみ使用されます。 Visual C# プロジェクトでは、式に C# が使用されるようになりました。 文法強調表示や Intellisense などの機能を備えた、フル機能の C# 式エディターが用意されています。 以前のバージョンで作成された、Visual Basic の式を使用する C# ワークフロー プロジェクトは引き続き動作します。  
  
 C# の式はデザイン時に検証されます。 C# 式のエラーは赤い波下線でマークされます。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] C# 式を参照してください[c# 式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md)です。  
  
###  <a name="BKMK_Visibility"></a> シェル バーおよびヘッダーの可視性の詳細に制御項目  
 再ホストされたデザイナーでは、標準 UI コントロールの中に、特定のワークフローにとって意味がないものもあれば、無効になっているものもあります。 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、このカスタマイズがデザイナーの下部のシェル バーのみでサポートされています。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、デザイナーの上部にあるシェルのヘッダー項目の表示は、適切な <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> 値で <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> を設定することにより調整できます。  
  
###  <a name="BKMK_AutoConnect"></a> 自動接続と自動挿入フローチャートおよびステート マシン ワークフロー  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、フローチャート ワークフロー内のノード間の接続は手動で追加する必要がありました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、フローチャート ノードとステート マシン ノードに自動接続ポイントがあり、これらのポイントは、アクティビティをツールボックスからデザイナー画面上にドラッグすると表示されます。 アクティビティをこれらのポイントのうち 1 つにドロップすると、アクティビティが必要な接続と共に自動的に追加されます。  
  
 次のスクリーンショットは、アクティビティがツールボックスからドラッグされるときに表示されるアタッチ ポイントを示します。  
  
 ![自動接続ポイントを示すフローチャートの開始ノード](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 アクティビティは、フローチャート ノードと状態の間の接続にドラッグすることで、その他 2 つのノード間にノードを自動挿入することもできます。 次のスクリーンショットは、アクティビティをツールボックスからドラッグ アンド ドロップできる、強調表示された接続線を示しています。  
  
 ![自動&#45;アクティビティをドロップするためのハンドルを挿入](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "自動")  
  
###  <a name="BKMK_Annotations"></a> デザイナー注釈  
 より大規模なワークフローの開発を容易にするため、デザイン プロセスを追跡できるよう注釈の追加がサポートされるようになりました。 注釈は、アクティビティ、状態、フローチャート ノード、変数、および引数に追加できます。 次のスクリーンショットは、デザイナーに注釈を追加するためのコンテキスト メニューを示しています。  
  
 ![注釈コンテキスト メニュー](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
### <a name="debugging-states"></a>デバッグ状態  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、アクティビティ以外の要素は、実行の単位ではないため、デバッグ ブレークポイントがサポートされていませんでした。 このリリースでは、<xref:System.Activities.Statements.State> オブジェクトにブレークポイントを追加する機能が用意されています。 ブレークポイントを <xref:System.Activities.Statements.State> に設定した場合、そのエントリ アクティビティまたはトリガーがスケジュールされる前に、状態が遷移すると実行が停止します。  
  
###  <a name="BKMK_ActivityDelegates"></a> 定義し、デザイナーでの ActivityDelegate オブジェクトの使用  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] のアクティビティでは、<xref:System.Activities.ActivityDelegate> オブジェクトを使用して、ワークフローの他の部分がワークフローの実行と対話できる実行ポイントを公開していましたが、通常、これらの実行ポイントを使用するには相当な量のコードが必要でした。 このリリースでは、開発者はワークフロー デザイナーを使用してアクティビティ デリゲートを定義および使用できます。 詳細については、次を参照してください。[する方法: 定義およびワークフロー デザイナーでアクティビティ デリゲートを使用する](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)です。  
  
###  <a name="BKMK_BuildTimeValidation"></a> ビルド時の検証  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、ワークフローの検証エラーが、ワークフロー プロジェクトのビルド中のビルド エラーとして数えられていませんでした。 つまり、ワークフローの検証エラーが発生した場合でも、ワークフロー プロジェクトのビルドは成功している可能性があります。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、ワークフローの検証エラーが発生するとビルドは失敗します。  
  
###  <a name="BKMK_DesignTimeValidation"></a> デザイン時バック グラウンド検証  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、ワークフローがフォアグラウンド プロセスとして検証されていました。これにより、複雑な検証プロセスや時間のかかる検証プロセスでは UI が応答を停止する可能性がありました。 現在、ワークフローの検証はバックグラウンド スレッドで実行されるため、UI がブロックされることはありません。  
  
###  <a name="BKMK_ViewState"></a> XAML ファイルで別の場所にあるビューステートします。  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、ワークフローのビューステート情報は、多くの異なる場所にある XAML ファイルに保存されていました。 これは、XAML を直接読み取ったり、ビューステート情報を削除するコードを記述したりする開発者にとっては不便です。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、XAML ファイルのビュー状態情報は、XAML ファイル内の個別の要素としてシリアル化します。  開発者ことが簡単を探し、アクティビティ、ビュー状態情報を編集ビュー ステートを完全に削除します。  
  
###  <a name="BKMK_ExpressionExtensibility"></a> 式の拡張性  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、開発者が、ワークフロー デザイナーにプラグインできる、独自の式および式作成操作を作成できるようになります。  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> 再ホストされたデザイナーでの Workflow 4.5 機能のオプトイン  
 下位互換性を維持するために、再ホストされたデザイナーでは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] に含まれる新機能の一部が既定で有効になっていません。 これは、再ホストされたデザイナーを使用する既存のアプリケーションが、最新バージョンに更新することで壊れないようにするためです。 再ホストされたデザイナーで新機能を有効にするには、<xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> を ".NET Framework 4.5" に設定するか、<xref:System.Activities.Presentation.DesignerConfigurationService> の各メンバーを設定して各機能を有効にします。  
  
##  <a name="BKMK_NewWFModels"></a> 新しいワークフロー開発モデル  
 このリリースには、フローチャートおよびシーケンシャル ワークフロー開発モデルに加えて、ステート マシンのワークフロー、およびコントラクト優先ワークフロー サービスが含まれています。  
  
###  <a name="BKMK_StateMachine"></a> ステート マシン ワークフロー  
 ステート マシン ワークフローは、.NET Framework 4 バージョン 4.0.1 の一部として導入された、 [Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092)です。 この更新プログラムには、開発者がステート マシンのワークフローを作成できるようにする、いくつかの新しいクラスとアクティビティが含まれていました。 これらのクラスおよびアクティビティは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 用に更新されました。 更新プログラムには次のものが含まれています。  
  
1.  状態にブレークポイントを設定する機能。  
  
2.  ワークフロー デザイナーで遷移をコピーして貼り付ける機能。  
  
3.  トリガーを共有する遷移の作成に対するデザイナーのサポート。  
  
4.  ステート マシンのワークフロー作成に使用するアクティビティ (<xref:System.Activities.Statements.StateMachine><xref:System.Activities.Statements.State>、<xref:System.Activities.Statements.Transition> など)。  
  
 次のスクリーン ショットから完成したステート マシン ワークフローを示しています、[チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)ステップ[する方法: ステート マシン ワークフローを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)です。  
  
 ![完成したステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 ステート マシン ワークフローを作成する方法の詳細については、次を参照してください。[ステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md)です。  
  
###  <a name="BKMK_ContractFirst"></a> コントラクト優先ワークフローの開発  
 コントラクト優先ワークフローの開発ツールでは、開発者が最初に、コードでコントラクトを設計し、Visual Studio での数回のクリックで各操作を表す、ツールボックスに自動的に活動テンプレートを生成できるようにします。 これらのアクティビティは、コントラクトで定義された操作を実装するワークフローを作成するために使用されます。 ワークフロー デザイナーは、ワークフロー サービスを検証し、これらの操作が実装され、ワークフローの署名がコントラクトの署名と一致することを確認します。 また、開発者は、ワークフロー サービスを、実装済みコントラクトのコレクションと関連付けることもできます。 コントラクト優先ワークフロー サービスの開発の詳細については、次を参照してください。[する方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)です。
