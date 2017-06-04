---
title: "方法 : Win32 ホスト コンテナーを使用してヒット テストを実行する | Microsoft Docs"
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
  - "ヒット テスト, 使用 (Win32 ホスト コンテナーを)"
  - "ビジュアル オブジェクト, ヒット テスト"
  - "Win32 ホスト コンテナー, ヒット テストに使用"
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : Win32 ホスト コンテナーを使用してヒット テストを実行する
ビジュアル オブジェクトのホスト ウィンドウ コンテナーを提供することで、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ウィンドウにビジュアル オブジェクトを作成できます。  格納されているビジュアル オブジェクト用のイベント処理機能を提供するには、ホスト ウィンドウ コンテナーのメッセージ フィルター ループに渡されるメッセージを処理します。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウでビジュアル オブジェクトをホストする方法の詳細については、「[チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)」を参照してください。  
  
## 使用例  
 次のコードでは、ビジュアル オブジェクトのホスト コンテナーとして使用される [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウにマウス イベント ハンドラーを設定する方法を示します。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 トラッピング固有のマウス イベントに対応して[ヒット テスト](GTMT)を設定する方法を次の例に示します。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 The <xref:System.Windows.Interop.HwndSource> オブジェクトは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ウィンドウ内の [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] コンテンツを表示します。<xref:System.Windows.Interop.HwndSource> オブジェクトの <xref:System.Windows.Interop.HwndSource.RootVisual%2A> プロパティの値は、[ビジュアル ツリー](GTMT)階層の最上位ノードを表します。  
  
 Win32 ホスト コンテナーを使用するオブジェクトのヒット テストのサンプル全体については、[Win32 相互運用によるヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159995)を参照してください。  
  
## 参照  
 <xref:System.Windows.Interop.HwndSource>   
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)