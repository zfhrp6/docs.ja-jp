---
title: 再ホストされたワークフロー デザイナーにおける Workflow Foundation 4.5 の新機能のサポート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a11a1cddbb5b65bf174cabe7774ad62791657f54
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>再ホストされたワークフロー デザイナーにおける Workflow Foundation 4.5 の新機能のサポート
Windows Workflow Foundation (WF) で[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]ワークフロー デザイナー エクスペリエンスにいくつかの拡張機能など、多くの新機能が導入されました。 このトピックでは、このような新機能のうち、再ホストされたデザイナーでサポートされている機能と現時点ではサポートされていない機能について詳しく説明します。  
  
> [!NOTE]
>  導入された新しい Windows Workflow Foundation (WF) 機能のすべての一覧については[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を含めているデザイナーのホスト変更に関連する、次を参照してください。 [.NET 4.5 での Windows Workflow Foundation の新](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)です。  
  
## <a name="activities"></a>アクティビティ  
 組み込みのアクティビティ ライブラリには、既存のアクティビティ用の新しいアクティビティと新しい機能が含まれています。 これらの新しいアクティビティはすべて、再ホストされたデザイナーでサポートされています。 これらの新しいアクティビティの詳細については、次を参照してください。、[アクティビティ](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_NewActivities)のセクション[.NET 4.5 での Windows Workflow Foundation の新](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)です。  
  
## <a name="c-expressions"></a>C# の式  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] より前のバージョンでは、ワークフロー内のすべての式を Visual Basic のみで記述できました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、Visual Basic の式は Visual Basic で作成されたプロジェクトでのみ使用されます。 Visual C# プロジェクトでは、式に C# が使用されるようになりました。 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] でワークフローを作成する場合、文法強調表示や Intellisense などの機能を備えた、フル機能の C# 式エディターが用意されています。 以前のバージョンで作成された、Visual Basic の式を使用する C# ワークフロー プロジェクトは引き続き動作します。  
  
> [!WARNING]
>  C# の式は、再ホストされたデザイナーではサポートされていません。  
  
## <a name="new-designer-capabilities"></a>デザイナーの新機能  
  
### <a name="designer-search"></a>デザイナーでの検索  
 [クイック検索](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind)と[ファイル内の検索](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles)で導入された機能[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]再ホストされたデザイナーでサポートされていません。 `Toolbox` による検索は、再ホストされたデザイナーでもサポートされています。 これらの機能の詳細については、次を参照してください。[デザイナーでの検索](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch)です。  
  
> [!WARNING]
>  [クイック検索](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind)と[ファイル内の検索](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles)再ホストされたデザイナーでサポートされていません。  
  
### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>変数デザイナーと引数デザイナーのコンテキスト メニューの [削除]  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、変数および引数を削除できるのは、デザイナーでキーボードを使用した場合のみでした。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、コンテキスト メニューを使用して変数および引数を削除できます。 この機能は、再ホストされたデザイナーでサポートされています。  
  
 変数デザイナーと引数デザイナーのコンテキスト メニューを次のスクリーンショットに示しています。  
  
 ![変数/引数デザイナーのコンテキスト メニュー](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
### <a name="auto-surround-with-sequence"></a>ブロックの自動挿入シーケンス  
 ワークフローまたは特定のコンテナー アクティビティ (<xref:System.Activities.Statements.NoPersistScope> など) には Body アクティビティを 1 つしか含めることができないため、2 つ目のアクティビティを追加するには、開発者が最初のアクティビティを削除し、<xref:System.Activities.Statements.Sequence> アクティビティを追加してから、シーケンス アクティビティに両方のアクティビティを追加する必要がありました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、デザイナー画面に 2 つ目のアクティビティを追加すると、`Sequence` アクティビティが自動的に作成され、両方のアクティビティがラップされます。 この機能は、再ホストされたデザイナーでサポートされています。  
  
 次のスクリーンショットは、`WriteLine` の `Body` 内の `NoPersistScope` アクティビティを示しています。  
  
 ![自動&#45;の格納場所を囲む](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 次のスクリーンショットは、2 つ目の `Sequence` を 1 つ目の下にドロップしたときに `Body` 内に自動的に作成された `WriteLine` アクティビティを示しています。  
  
 ![自動的に作成された sequence アクティビティ](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
### <a name="pan-mode"></a>パン モード  
 デザイナーで大規模なワークフロー内をより簡単に移動するには、パン モードを有効にすると、開発者は、スクロール バーを使用する必要なく、ワークフローの表示される部分をクリックおよびドラッグして移動できるようになります。 パン モードをアクティブ化するボタンは、デザイナーの右下隅にあります。 この機能は、再ホストされたデザイナーでサポートされています。  
  
 次のスクリーンショットは、ワークフロー デザイナーの右下隅にあるパン ボタンを示しています。  
  
 ![ワークフロー デザイナーで [パン] ボタン](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 マウスの中央ボタンまたは Space キーを使用して、ワークフロー デザイナーをパンすることもできます。  
  
### <a name="multi-select"></a>複数選択  
 複数のアクティビティを同時に選択できます。これを行うには、複数のアクティビティを囲むようにドラッグするか (パン モードが無効な場合)、Ctrl キーを押したまま目的のアクティビティを 1 つずつクリックします。 この機能は、再ホストされたデザイナーでサポートされています。  
  
 選択した複数のアクティビティは、デザイナー内でドラッグ アンド ドロップすることも、コンテキスト メニューを使用して操作することもできます。  
  
### <a name="outline-view-of-workflow-items"></a>ワークフロー項目のアウトライン表示  
 階層ワークフローを移動しやすくするため、ワークフローのコンポーネントはツリー スタイルのアウトライン表示で示されます。 アウトライン表示で、 **ドキュメント アウトライン**ビュー。 上部のメニューから、Visual Studio で、このビューを開く、次のように選択します**ビュー**、**その他のウィンドウ**、 **ドキュメント アウトライン**、または Ctrl W キーと u です。 キーを押します。 アウトライン表示でノードをクリックすると、ワークフロー デザイナーの対応するアクティビティに移動し、アウトライン表示が更新されて、デザイナーで選択されているアクティビティが表示されます。 この機能は、再ホストされたデザイナーでサポートされています。  
  
 完了済みワークフローからの次のスクリーン ショット、[チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)シーケンシャル ワークフローにより、アウトライン表示を示しています。  
  
 ![ワークフロー デザイナーでビューをアウトライン](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>シェル バーおよびヘッダー項目の可視性の詳細な制御  
 再ホストされたデザイナーでは、標準 UI コントロールの中に、特定のワークフローにとって意味がないものもあれば、無効になっているものもあります。 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、このカスタマイズがデザイナーの下部のシェル バーのみでサポートされています。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、デザイナーの上部にあるシェルのヘッダー項目の表示は、適切な <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> 値で <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> を設定することにより調整できます。  
  
### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>フローチャートおよびステート マシンのワークフローの自動接続と自動挿入  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、フローチャート ワークフロー内のノード間の接続は手動で追加する必要がありました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、フローチャート ノードとステート マシン ノードに自動接続ポイントがあり、これらのポイントは、アクティビティをツールボックスからデザイナー画面上にドラッグすると表示されます。 アクティビティをこれらのポイントのうち 1 つにドロップすると、アクティビティが必要な接続と共に自動的に追加されます。  
  
 次のスクリーンショットは、アクティビティがツールボックスからドラッグされるときに表示されるアタッチ ポイントを示します。  
  
 ![自動接続ポイントを示すフローチャートの開始ノード](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 アクティビティは、フローチャート ノードと状態の間の接続にドラッグすることで、その他 2 つのノード間にノードを自動挿入することもできます。 次のスクリーンショットは、アクティビティをツールボックスからドラッグ アンド ドロップできる、強調表示された接続線を示しています。  
  
 ![自動&#45;アクティビティをドロップするためのハンドルを挿入](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "自動")  
  
 自動接続と自動挿入は、再ホストされたデザイナーでサポートされています。  
  
### <a name="designer-annotations"></a>デザイナー注釈  
 より大規模なワークフローの開発を容易にするため、デザイン プロセスを追跡できるよう注釈の追加がサポートされるようになりました。 注釈は、アクティビティ、状態、フローチャート ノード、変数、および引数に追加できます。 次のスクリーンショットは、デザイナーに注釈を追加するためのコンテキスト メニューを示しています。  
  
 ![注釈コンテキスト メニュー](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
 デザイナー注釈は、再ホストされたデザイナーでサポートされています。  
  
### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>デザイナーでの ActivityDelegate オブジェクトの定義と使用  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] のアクティビティでは、<xref:System.Activities.ActivityDelegate> オブジェクトを使用して、ワークフローの他の部分がワークフローの実行と対話できる実行ポイントを公開していましたが、通常、これらの実行ポイントを使用するには相当な量のコードが必要でした。 このリリースでは、開発者はワークフロー デザイナーを使用してアクティビティ デリゲートを定義および使用できます。 詳細については、次を参照してください。[する方法: 定義およびワークフロー デザイナーでアクティビティ デリゲートを使用する](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)です。  
  
 アクティビティ デリゲートは、再ホストされたデザイナーでサポートされています。  
  
### <a name="build-time-validation"></a>ビルド時の検証  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、ワークフローの検証エラーが、ワークフロー プロジェクトのビルド中のビルド エラーとして数えられていませんでした。 つまり、ワークフローの検証エラーが発生した場合でも、ワークフロー プロジェクトのビルドは成功している可能性があります。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、ワークフローの検証エラーが発生するとビルドは失敗します。  
  
> [!WARNING]
>  ビルド時の検証は、再ホストされたデザイナーではサポートされていません。  
  
### <a name="design-time-background-validation"></a>デザイン時バックグラウンド検証  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、ワークフローがフォアグラウンド プロセスとして検証されていました。これにより、複雑な検証プロセスや時間のかかる検証プロセスでは UI が応答を停止する可能性がありました。 現在、ワークフローの検証はバックグラウンド スレッドで実行されるため、UI がブロックされることはありません。  
  
 デザイン時バックグラウンド検証は、再ホストされたデザイナーでサポートされています。  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>XAML ファイル内で別々の場所にあるビューステート  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] では、ワークフローのビューステート情報は、多くの異なる場所にある XAML ファイルに保存されていました。 これは、XAML を直接読み取ったり、ビューステート情報を削除するコードを記述したりする開発者にとっては不便です。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、XAML ファイルのビュー状態情報は、XAML ファイル内の個別の要素としてシリアル化します。  開発者ことが簡単を探し、アクティビティ、ビュー状態情報を編集ビュー ステートを完全に削除します。  
  
 この機能は、再ホストされたワークフロー デザイナーでサポートされています。  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>再ホストされたデザイナーでの Workflow 4.5 機能のオプトイン  
 下位互換性を維持するために、再ホストされたデザイナーでは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] に含まれる新機能の一部が既定で有効になっていません。 これは、再ホストされたデザイナーを使用する既存のアプリケーションが、最新バージョンに更新することで壊れないようにするためです。 再ホストされたデザイナーで新機能を有効にするには、<xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> を ".Net Framework 4.5" に設定するか、<xref:System.Activities.Presentation.DesignerConfigurationService> の各メンバーを設定して各機能を有効にします。  
  
## <a name="new-workflow-development-models"></a>新しいワークフロー開発モデル  
 このリリースには、フローチャートおよびシーケンシャル ワークフロー開発モデルに加えて、ステート マシンのワークフロー、およびコントラクト優先ワークフロー サービスが含まれています。  
  
### <a name="state-machine-workflows"></a>ステート マシンのワークフロー  
 ステート マシン ワークフローは、.NET Framework 4.0.1 の一部として導入された、 [Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092)です。 この更新プログラムには、開発者がステート マシンのワークフローを作成できるようにする、いくつかの新しいクラスとアクティビティが含まれていました。 これらのクラスおよびアクティビティは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 用に更新されました。 更新プログラムには次のものが含まれています。  
  
1.  状態にブレークポイントを設定する機能。  
  
2.  ワークフロー デザイナーで遷移をコピーして貼り付ける機能。  
  
3.  トリガーを共有する遷移の作成に対するデザイナーのサポート。  
  
4.  ステート マシンのワークフロー作成に使用するアクティビティ (<xref:System.Activities.Statements.StateMachine><xref:System.Activities.Statements.State>、<xref:System.Activities.Statements.Transition> など)。  
  
 次のスクリーン ショットから完成したステート マシン ワークフローを示しています、[チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)ステップ[する方法: ステート マシン ワークフローを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)です。  
  
 ![完成したステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 ステート マシン ワークフローを作成する方法の詳細については、次を参照してください。[ステート マシン ワークフロー](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md)です。 ステート マシンのワークフローは、再ホストされたデザイナーでサポートされています。  
  
### <a name="contract-first-workflow-development"></a>コントラクト優先ワークフローの開発  
 コントラクト優先ワークフローの開発ツールでは、開発者が最初に、コードでコントラクトを設計し、Visual Studio での数回のクリックで各操作を表す、ツールボックスに自動的に活動テンプレートを生成できるようにします。 これらのアクティビティは、コントラクトで定義された操作を実装するワークフローを作成するために使用されます。 ワークフロー デザイナーは、ワークフロー サービスを検証し、これらの操作が実装され、ワークフローの署名がコントラクトの署名と一致することを確認します。 また、開発者は、ワークフロー サービスを、実装済みコントラクトのコレクションと関連付けることもできます。 コントラクト優先ワークフロー サービスの開発の詳細については、次を参照してください。[する方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)です。  
  
> [!WARNING]
>  コントラクト優先ワークフローの開発は、ワークフロー デザイナーではサポートされていません。
