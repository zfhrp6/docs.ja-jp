---
title: "方法 : Win32 ホスト コンテナーを使用してヒット テストを実行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142c2faa01c32ac6602e80eaef18779f93154aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>方法 : Win32 ホスト コンテナーを使用してヒット テストを実行する
内でビジュアル オブジェクトを作成することができます、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ウィンドウではビジュアル オブジェクトをホスト ウィンドウ コンテナーを提供します。 格納されているビジュアル オブジェクト用のイベント処理機能を提供するには、ホスト ウィンドウ コンテナーのメッセージ フィルター ループに渡されるメッセージを処理します。 参照してください[チュートリアル: Win32 アプリケーションでビジュアル オブジェクトをホストしている](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)ビジュアル オブジェクトをホストする方法について、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウです。  
  
## <a name="example"></a>例  
 次のコードのマウス イベントのハンドラーを設定する方法を示しています、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ビジュアル オブジェクトのホストのコンテナーとして使用するウィンドウです。  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 次の例では、固有のマウス イベントをトラップへの応答でヒット テストを設定する方法を示します。  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource>オブジェクトが表して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]内のコンテンツの[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ウィンドウです。 値、<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>オブジェクトがビジュアル ツリー階層内の最上位のノードを表します。  
  
 ヒット テストの完全なサンプルは、Win32 ホスト コンテナーを使用してオブジェクトを参照してください[ヒット テストの相互運用の Win32 サンプルを](http://go.microsoft.com/fwlink/?LinkID=159995)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Interop.HwndSource>  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
