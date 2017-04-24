---
title: "方法 : UI を返すアドインを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アドイン [WPF], 返す (UI を)"
  - "作成 (UI を返すアドインを) [WPF]"
  - "実装 (アドイン パイプライン セグメントを) [WPF]"
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : UI を返すアドインを作成する
この例では、ホスト [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] スタンドアロン アプリケーションに [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を返すアドインを作成する方法を示します。  
  
 このアドインが返す[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ユーザー コントロールです。  ユーザー コントロールの中身は単一のボタンで、クリックするとメッセージ ボックスを表示します。  このアドインは [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] スタンドアロン アプリケーションがホストし、アドインが返すユーザー コントロールをメイン アプリケーション ウィンドウのコンテンツとして表示します。  
  
 **必要条件**  
  
 この例では、このシナリオを実現する [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 拡張機能に焦点を当てます。前提条件は次のとおりです。  
  
-   パイプライン、アドイン、ホスト開発など、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルについて知っていること。  これらの概念の詳細については、「[アドインおよび拡張機能](../../../../ml/index.xml)」を参照してください。  パイプライン、アドイン、およびホスト アプリケーションの実装例を示すチュートリアルについては、「[チュートリアル : 拡張性のあるアプリケーションの作成](../Topic/Walkthrough:%20Creating%20an%20Extensible%20Application.md)」を参照してください。  
  
-   [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 拡張機能について知っていること。詳細については、「[WPF アドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)」を参照してください。  
  
## 使用例  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返すアドインを作成するには、各パイプライン セグメント、アドイン、およびホスト アプリケーションに特定のコードが必要です。  
  
   
  
<a name="Contract"></a>   
## コントラクト パイプライン セグメントの実装  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返すようにするには、メソッドはコントラクトで宣言し、その戻り値を <xref:System.AddIn.Contract.INativeHandleContract> 型にする必要があります。  次のコードではこれについて、`IWPFAddInContract` コントラクトの `GetAddInUI` メソッドによって示します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## アドイン ビュー パイプライン セグメントの実装  
 アドインは [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を実装するため、<xref:System.Windows.FrameworkElement> のサブクラスとして提供します。`IWPFAddInView.GetAddInUI` に関連するアドイン ビューのメソッドは <xref:System.Windows.FrameworkElement> 型の値を返す必要があります。  次のコードでは、コントラクトのアドイン ビューがインターフェイスとして実装されています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## アドイン側アダプター パイプライン セグメントの実装  
 コントラクト メソッドは <xref:System.AddIn.Contract.INativeHandleContract> を返しますが、アドインは <xref:System.Windows.FrameworkElement> を返します \(アドイン ビューの指定のとおり\)。  したがって、<xref:System.Windows.FrameworkElement> は、分離境界を越える前に <xref:System.AddIn.Contract.INativeHandleContract> に変換される必要があります。  この処理は、次のコードに示すように、アドイン側のアダプターで <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> を呼び出して実行されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## ホスト ビュー パイプライン セグメントの実装  
 ホスト アプリケーションは <xref:System.Windows.FrameworkElement> を表示するため、`IWPFAddInHostView.GetAddInUI` に関連するホスト ビューのメソッドは <xref:System.Windows.FrameworkElement> 型の値を返す必要があります。  次のコードでは、コントラクトのホスト ビューがインターフェイスとして実装されています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## ホスト側アダプター パイプライン セグメントの実装  
 コントラクト メソッドは <xref:System.AddIn.Contract.INativeHandleContract> を返しますが、ホスト アプリケーションでは <xref:System.Windows.FrameworkElement> が想定されています \(ホスト ビューの指定のとおり\)。  したがって、<xref:System.AddIn.Contract.INativeHandleContract> は、分離境界を越えた後に <xref:System.Windows.FrameworkElement> に変換される必要があります。  この処理は、次のコードに示されているように、ホスト側のアダプターで <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> を呼び出して実行されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## アドインの実装  
 アドイン側のアダプターとアドイン ビューを作成したら、アドイン \(`WPFAddIn1.AddIn`\) に `IWPFAddInView.GetAddInUI` メソッドを実装して、<xref:System.Windows.FrameworkElement> オブジェクト \(この例では <xref:System.Windows.Controls.UserControl>\) を返すようにする必要があります。  <xref:System.Windows.Controls.UserControl> \(`AddInUI`\) は次のコードに示すように実装します。  
  
 [!code-xml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 アドインの `IWPFAddInView.GetAddInUI` の実装では、次のコードに示すように、`AddInUI` の新しいインスタンスを返すだけです。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## ホスト アプリケーションの実装  
 ホスト側のアダプターとホスト ビューが作成されると、ホスト アプリケーションで [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを使用して、パイプラインを開き、アドインのビューを取得し、`IWPFAddInHostView.GetAddInUI` メソッドを呼び出すことができます。  これらの手順を次にコードに示します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## 参照  
 [アドインおよび拡張機能](../../../../ml/index.xml)   
 [WPF アドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)