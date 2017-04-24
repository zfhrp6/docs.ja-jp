---
title: "チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ホスティング, ビジュアル オブジェクト (Win32 コードの)"
  - "ビジュアル オブジェクト (Win32 コードの)"
  - "Win32 コード, ビジュアル オブジェクト"
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。  ただし、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] コードに多くの投資を行った場合は、コードを記述し直すよりも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能をアプリケーションに追加する方が、より効率的である場合があります。  アプリケーション内で現在使用されている [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィック サブシステムのサポートを提供するため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウのオブジェクトをホストする機能を提供します。  
  
 このチュートリアルでは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ビジュアル オブジェクトをホストするサンプル アプリケーション \([Win32 相互運用によるヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159995)\) を記述する方法を説明します。  
  
   
  
<a name="requirements"></a>   
## 要件  
 このチュートリアルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] および [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] のプログラミングに関する基本的な知識があることを前提としています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プログラミングの概要については、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの概要については多数の書籍が出版されていますので、それらを参照してください。特に『プログラミング Windows』\(Charles Petzold 著\) が参考になります。  
  
> [!NOTE]
>  このチュートリアルには、関連するサンプルからのコード例が数多く含まれています。  ただし、読みやすさのために、完全なサンプル コードは含まれていません。  サンプル コード全体については、[Win32 相互運用によるヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159995)を参照してください。  
  
<a name="creating_the_host_win32_window"></a>   
## ホスト Win32 ウィンドウの作成  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトをホストするキーとなるのは、<xref:System.Windows.Interop.HwndSource> クラスです。  このクラスは [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトをラップし、そのオブジェクトを子ウィンドウとして [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に組み込むことができます。  
  
 次の例では、ビジュアル オブジェクトの [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテナー ウィンドウとして <xref:System.Windows.Interop.HwndSource> オブジェクトを作成するためのコードを示します。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウのウィンドウ スタイル、位置、およびその他のパラメーターを設定する場合は、<xref:System.Windows.Interop.HwndSourceParameters> オブジェクトを使用します。  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> プロパティの値を WS\_EX\_TRANSPARENT に設定することはできません。  これは、ホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウを透明にできないことを意味します。  このため、ホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの背景色はその親ウィンドウと同じ背景色に設定されます。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## ホスト Win32 ウィンドウへのビジュアル オブジェクトの追加  
 ビジュアル オブジェクトのホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテナー ウィンドウを作成したら、そのコンテナー ウィンドウにビジュアル オブジェクトを追加できます。  アニメーションなどでビジュアル オブジェクトが変形しても、ビジュアル オブジェクトがホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの境界を示す四角形を超えて拡大されないようにする必要があります。  
  
 次の例では、<xref:System.Windows.Interop.HwndSource> オブジェクトを作成し、ビジュアル オブジェクトを追加するコードを示します。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource> オブジェクトの <xref:System.Windows.Interop.HwndSource.RootVisual%2A> プロパティが、ホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウに追加される最初のビジュアル オブジェクトに設定されます。  ルートのビジュアル オブジェクトによりビジュアル オブジェクト ツリーの最上位ノードが定義されます。  ホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウに追加される後続のビジュアル オブジェクトは、子オブジェクトとして追加されます。  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## Win32 メッセージ フィルターの実装  
 ビジュアル オブジェクトのホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウでは、アプリケーション キューからウィンドウに送信されるメッセージを処理するために、ウィンドウ メッセージのフィルター プロシージャが必要です。  ウィンドウ プロシージャは [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] システムからのメッセージを受け取ります。  受け取るメッセージは、入力メッセージまたはウィンドウ管理メッセージです。  ウィンドウ プロシージャでメッセージを処理するか、システムにメッセージを渡して既定の処理を行うこともできます。  
  
 ビジュアル オブジェクトの親として定義した <xref:System.Windows.Interop.HwndSource> オブジェクトは、提供するウィンドウ メッセージのフィルター プロシージャを参照する必要があります。  <xref:System.Windows.Interop.HwndSource> オブジェクトを作成する場合は、<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> プロパティがウィンドウ プロシージャを参照するように設定します。  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 次の例では、左右のマウス ボタンのメッセージを処理するコードを示します。  マウスのヒット位置の座標値は、`lParam`パラメーターの値に格納されます。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## Win32 メッセージの処理  
 次のコード例では、ホスト [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウに格納されたビジュアル オブジェクトの階層に対して、ヒット テストがどのように実行されるかを示します。  <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> メソッドを使用することにより、ビジュアル オブジェクトのジオメトリ内にポイントがあるかどうかを識別して、ヒット テストを実行するルートのビジュアル オブジェクトと座標値を指定できます。  この場合、ルートのビジュアル オブジェクトは、<xref:System.Windows.Interop.HwndSource> オブジェクトの <xref:System.Windows.Interop.HwndSource.RootVisual%2A> プロパティの値です。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 ビジュアル オブジェクトに対するヒット テストの詳細については、「[ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Interop.HwndSource>   
 [Win32 相互運用によるヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159995)   
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)