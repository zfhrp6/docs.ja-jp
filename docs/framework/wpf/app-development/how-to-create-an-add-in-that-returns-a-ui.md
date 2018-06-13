---
title: '方法 : UI を返すアドインを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: 24b30d61553796840a44a869eacb33232a0b78d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548234"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>方法 : UI を返すアドインを作成する
この例をホストする Windows Presentation Foundation (WPF) を返すようなアドインを作成する方法を示しています。[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロン アプリケーションです。  
  
 アドインを返します、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]されている、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ユーザー コントロールです。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロン アプリケーションがアドインをホストし、アプリケーションのメイン ウィンドウの内容として (アドインによって返される) ユーザー コントロールを表示します。  
  
 **必須コンポーネント**  
  
 この例を強調表示、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張機能を[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインでは、このシナリオを有効にし、モデルを次を前提としています。  
  
-   ナレッジ、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインなど、モデル パイプライン、アドインでは、ホストの開発。 これらの概念に慣れていない場合は、次を参照してください。[アドインおよび拡張](../../../../docs/framework/add-ins/index.md)です。 パイプライン、アドイン、およびホスト アプリケーションの実装を示すチュートリアルでは、次を参照してください。[チュートリアル: 拡張性のあるアプリケーションを作成する](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)です。  
  
-   ナレッジ、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張機能を[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインでは、モデルをご覧ください: [WPF のアドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)です。  
  
## <a name="example"></a>例  
 アドインを表すオブジェクトを作成する、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]パイプラインの各セグメント、アドイン、およびホスト アプリケーションの特定のコードが必要です。  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装  
 メソッドを返すためのコントラクトを定義する必要があります、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、その戻り値型でなければなりませんと<xref:System.AddIn.Contract.INativeHandleContract>です。 示されるこれは、`GetAddInUI`のメソッド、`IWPFAddInContract`次のコード コントラクトします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装  
 アドインが実装されているため、[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]のサブクラスとして提供<xref:System.Windows.FrameworkElement>に対応する追加のビューのメソッドは、`IWPFAddInView.GetAddInUI`型の値を返す必要があります<xref:System.Windows.FrameworkElement>です。 次のコードは、コントラクトのアドイン ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装  
 コントラクト メソッドを返します、 <xref:System.AddIn.Contract.INativeHandleContract>、アドインを返しますが、 <xref:System.Windows.FrameworkElement> (指定に従って、追加のビュー)。 その結果、<xref:System.Windows.FrameworkElement>に変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>分離境界を横断する前にします。 呼び出して追加側アダプターでこの作業を行う<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装  
 ホスト アプリケーションが表示されるため、<xref:System.Windows.FrameworkElement>に対応するホスト ビューのメソッドは、`IWPFAddInHostView.GetAddInUI`型の値を返す必要があります<xref:System.Windows.FrameworkElement>です。 次のコードは、コントラクトのホスト ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装  
 コントラクト メソッドを返します、 <xref:System.AddIn.Contract.INativeHandleContract>、ホスト アプリケーションが必要ですが、 <xref:System.Windows.FrameworkElement> (ホスト ビューで、指定した)。 その結果、<xref:System.AddIn.Contract.INativeHandleContract>に変換する必要があります、<xref:System.Windows.FrameworkElement>後、分離境界を越えます。 呼び出すことによって、ホスト側アダプターでこの作業を行う<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>アドインの実装  
 アドイン側アダプターとアドインのビューが作成されると、アドイン (`WPFAddIn1.AddIn`) を実装する必要があります、`IWPFAddInView.GetAddInUI`を返すメソッドを<xref:System.Windows.FrameworkElement>オブジェクト (、<xref:System.Windows.Controls.UserControl>この例では)。 実装、 <xref:System.Windows.Controls.UserControl>、 `AddInUI`、次のコードで表示されます。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 実装、 `IWPFAddInView.GetAddInUI` 、アドインで必要があるだけの新しいインスタンスを返す`AddInUI`、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装  
 ホスト側アダプターと作成されたホスト ビューでは、ホスト アプリケーションを使用して、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドイン モデルをパイプラインを開き、アドイン、および呼び出しのホスト ビューの取得、`IWPFAddInHostView.GetAddInUI`メソッドです。 これらの手順を次のコードに示します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>関連項目  
 [アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)  
 [WPF のアドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
