---
title: '方法 : UI であるアドインを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 4bd03c2f879ecab83306bb68552c044a33f2e6e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549592"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>方法 : UI であるアドインを作成する
この例は、Windows Presentation Foundation (WPF) によってホストされているは、アドインを作成する方法を示しています、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロン アプリケーションです。  
  
 アドインでは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]されている、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ユーザー コントロールです。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロン アプリケーションをホストにアドイン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]アプリケーションのメイン ウィンドウの内容として。  
  
 **必須コンポーネント**  
  
 この例を強調表示、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張機能を[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインでは、このシナリオを有効にし、モデルを次を前提としています。  
  
-   ナレッジ、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインなど、モデル パイプライン、アドインでは、ホストの開発。 これらの概念に慣れていない場合は、次を参照してください。[アドインおよび拡張](../../../../docs/framework/add-ins/index.md)です。 パイプライン、アドイン、およびホスト アプリケーションの実装を示すチュートリアルでは、次を参照してください。[チュートリアル: 拡張性のあるアプリケーションを作成する](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)です。  
  
-   ナレッジ、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張機能を[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインでは、モデルをご覧ください: [WPF のアドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)です。  
  
## <a name="example"></a>例  
 アドインを作成する、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]パイプラインの各セグメント、アドイン、およびホスト アプリケーションの特定のコードが必要です。  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装  
 アドインがの場合、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、アドインのコントラクトを実装する必要があります<xref:System.AddIn.Contract.INativeHandleContract>です。 例では、`IWPFAddInContract`実装<xref:System.AddIn.Contract.INativeHandleContract>、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装  
 アドインはのサブクラスとして実装されるため、<xref:System.Windows.FrameworkElement>型、アドインを表示する必要がありますもサブクラス<xref:System.Windows.FrameworkElement>です。 次のコードは、アドインのビューとして実装された、コントラクト、`WPFAddInView`クラスです。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 ここでは、アドイン ビューに由来<xref:System.Windows.Controls.UserControl>です。 そのため、アドインを[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]から派生することも<xref:System.Windows.Controls.UserControl>します。  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装  
 コントラクトは、 <xref:System.AddIn.Contract.INativeHandleContract>、アドインでは、 <xref:System.Windows.FrameworkElement> (で指定したビューでは、追加のパイプライン セグメント)。 したがって、<xref:System.Windows.FrameworkElement>に変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>分離境界を横断する前にします。 呼び出して追加側アダプターでこの作業を行う<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 返すアドインをアドイン モデルで、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (を参照してください[、アドインを返すことは、UI 作成](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md))、アドイン アダプターの変換、<xref:System.Windows.FrameworkElement>を<xref:System.AddIn.Contract.INativeHandleContract>を呼び出して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>です。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 必要があります呼び出すことも、このモデルでが、それを呼び出すコードを記述するメソッドを実装する必要があります。 オーバーライドすることで、これを行う<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>を呼び出すコードを実装して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>場合、コードを呼び出している<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>が想定している、<xref:System.AddIn.Contract.INativeHandleContract>です。 この場合、呼び出し元はホスト側のアダプターであり、これについては、後で説明します。  
  
> [!NOTE]
>  オーバーライドする必要があります<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>ホスト アプリケーション間のタブ移動を有効にするには、このモデルで[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]およびアドイン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 詳細については、WPF アドインの制限事項」を参照してください[WPF アドイン概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)です。  
  
 アドイン側アダプターから派生したインターフェイスを実装するため<xref:System.AddIn.Contract.INativeHandleContract>も実装する必要があります<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>は無視されますが、ときに<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>はオーバーライドします。  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装  
 このモデルでは、ホスト アプリケーション通常が必要ですが、ホスト ビューである、<xref:System.Windows.FrameworkElement>サブクラスです。 ホスト側のアダプターに変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>を<xref:System.Windows.FrameworkElement>後、<xref:System.AddIn.Contract.INativeHandleContract>分離の境界を越えます。 メソッドは、ホスト アプリケーションを取得するによって呼び出されるされていないため、 <xref:System.Windows.FrameworkElement>、ホスト ビュー返す必要があります""、<xref:System.Windows.FrameworkElement>でそれを含むです。 そのため、ホスト ビューは、のサブクラスから派生しなければなりません<xref:System.Windows.FrameworkElement>他を持つことができる[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]など<xref:System.Windows.Controls.UserControl>です。 次のコードは、ホスト ビューとして実装されたコントラクトの`WPFAddInHostView`クラスです。  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装  
 コントラクトは、 <xref:System.AddIn.Contract.INativeHandleContract>、ホスト アプリケーションが必要ですが、 <xref:System.Windows.Controls.UserControl> (ホスト ビューで、指定した)。 その結果、<xref:System.AddIn.Contract.INativeHandleContract>に変換する必要があります、<xref:System.Windows.FrameworkElement>ホスト ビューのコンテンツとして設定する前に、分離境界を横断する後 (から派生した<xref:System.Windows.Controls.UserControl>)。  
  
 この作業は、次のコードに示されているように、ホスト側アダプターによって行われます。  
  
  
  
 ホスト側のアダプターを取得すると、<xref:System.AddIn.Contract.INativeHandleContract>を呼び出して追加側アダプターの<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>メソッド (これは、ポイントで、<xref:System.AddIn.Contract.INativeHandleContract>分離境界を越える)。  
  
 ホスト側のアダプターが次に、変換、<xref:System.AddIn.Contract.INativeHandleContract>を<xref:System.Windows.FrameworkElement>を呼び出して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>です。 最後に、<xref:System.Windows.FrameworkElement>はホスト ビューのコンテンツとして設定します。  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>アドインの実装  
 アドイン側アダプターとアドイン ビューが用意できると、次のコードに示されているように、アドイン ビューから派生することでアドインを実装できます。  
  
  
  
  
  
 この例では、このモデルの 1 つの興味深い利点を確認できます: アドインに実装するだけで追加の開発者 (であるため、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]も)、アドインのクラスおよびアドインの両方ではなく[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装  
 ホスト側アダプターと作成されたホスト ビューでは、ホスト アプリケーションを使用して、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドイン モデルにパイプラインを開き、アドインのホスト ビューを取得します。 これらの手順を次のコードに示します。  
  
  
  
 ホスト アプリケーションで一般的な使用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドイン モデルでアクティブにするコード、アドインに暗黙的に、ホスト アプリケーションを [ホスト] ビューを返します。 ホスト アプリケーションには、その後ホスト ビューが表示されます (これは、 <xref:System.Windows.Controls.UserControl>) から、<xref:System.Windows.Controls.Grid>です。  
  
 アドインとの対話処理のコード[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]アドインのアプリケーション ドメインで実行します。 このような対話には、次のようなものがあります。  
  
-   処理、 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
-   表示、<xref:System.Windows.MessageBox>です。  
  
 このアクティビティは、ホスト アプリケーションから完全に分離されています。  
  
## <a name="see-also"></a>関連項目  
 [アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)  
 [WPF のアドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
