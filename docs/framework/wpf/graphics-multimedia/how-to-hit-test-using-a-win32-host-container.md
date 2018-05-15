---
title: '方法 : Win32 ホスト コンテナーを使用してヒット テストを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: 01c6a9dad6fccb38be4f240d0900727f776fd2b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="12b76-102">方法 : Win32 ホスト コンテナーを使用してヒット テストを実行する</span><span class="sxs-lookup"><span data-stu-id="12b76-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="12b76-103">内でビジュアル オブジェクトを作成することができます、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ウィンドウではビジュアル オブジェクトをホスト ウィンドウ コンテナーを提供します。</span><span class="sxs-lookup"><span data-stu-id="12b76-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="12b76-104">格納されているビジュアル オブジェクト用のイベント処理機能を提供するには、ホスト ウィンドウ コンテナーのメッセージ フィルター ループに渡されるメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="12b76-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="12b76-105">参照してください[チュートリアル: Win32 アプリケーションでビジュアル オブジェクトをホストしている](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)ビジュアル オブジェクトをホストする方法について、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="12b76-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12b76-106">例</span><span class="sxs-lookup"><span data-stu-id="12b76-106">Example</span></span>  
 <span data-ttu-id="12b76-107">次のコードのマウス イベントのハンドラーを設定する方法を示しています、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ビジュアル オブジェクトのホストのコンテナーとして使用するウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="12b76-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="12b76-108">次の例では、固有のマウス イベントをトラップへの応答でヒット テストを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12b76-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="12b76-109"><xref:System.Windows.Interop.HwndSource>オブジェクトが表して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]内のコンテンツの[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="12b76-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="12b76-110">値、<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>オブジェクトがビジュアル ツリー階層内の最上位のノードを表します。</span><span class="sxs-lookup"><span data-stu-id="12b76-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="12b76-111">ヒット テストの完全なサンプルは、Win32 ホスト コンテナーを使用してオブジェクトを参照してください[ヒット テストの相互運用の Win32 サンプルを](http://go.microsoft.com/fwlink/?LinkID=159995)です。</span><span class="sxs-lookup"><span data-stu-id="12b76-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b76-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="12b76-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="12b76-113">ビジュアル層でのヒット テスト</span><span class="sxs-lookup"><span data-stu-id="12b76-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="12b76-114">チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト</span><span class="sxs-lookup"><span data-stu-id="12b76-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
