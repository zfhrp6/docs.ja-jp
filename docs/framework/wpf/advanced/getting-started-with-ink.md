---
title: "インクの概要"
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
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c977e8a4a23f9739541cf28d9e34ad9e8db1daf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-ink"></a>インクの概要
デジタル インクを組み込むことをアプリケーションには、これまでよりも簡単です。 インクのプログラミングに完全な統合を実現するための COM および Windows フォームのメソッドへの推論の進化に伴い、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 個別の Sdk またはランタイム ライブラリをインストールする必要はありません。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 次の例を使用する、Microsoft Visual Studio 2005 をインストールする必要があります最初、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]です。 また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対応するアプリケーションの作成方法も理解しておく必要があります。 概要の詳細については、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。  
  
## <a name="quick-start"></a>クイック スタート  
 このセクションでは、単純なを作成できます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インクを収集するアプリケーション。  
  
 完了していない場合は、Microsoft Visual Studio 2005 をインストールし、[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション通常コンパイルする必要が、それらを表示する前にのみで構成されている場合でも[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。 ただし、[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]を実装するプロセスを高速化するように設計 XamlPad のアプリケーションが含まれています、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-ベースの UI。 そのアプリケーションを使用して、表示およびこのドキュメントで最初のいくつかのサンプルを修正することができます。 作成プロセスからコンパイルされたアプリケーション[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、このドキュメントの後半で説明します。  
  
 XAMLPad を起動する をクリックして、**開始** メニューのをポイント**すべてのプログラム**、 をポイント**ボタンをクリック**、指す**ツール**、 をクリック**XAMLPad**です。 表示ウィンドウでは、XAMLPad は、コード ペインで記述された XAML コードを表示します。 XAML コードを編集することができ、変更はすぐに表示ウィンドウで表示します。  
  
#### <a name="got-ink"></a>インクを取得します。  
 初めて開始する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インクをサポートするアプリケーション。  
  
1.  Microsoft Visual Studio 2005 を開きます。  
  
2.  新しい**Windows アプリケーション (WPF)**  
  
3.  型`<InkCanvas/>`間、`<Grid>`タグ  
  
4.  キーを押して**f5 キーを押して**デバッガーでアプリケーションを起動するには  
  
5.  スタイラスおよびマウスを使用して、記述**hello world**  ウィンドウで  
  
 相当するインクのみ 12 回のキーストロークで"hello world"アプリケーションを作成した!  
  
#### <a name="spice-up-your-application"></a>アプリケーションを楽しくする. します。  
 一部の機能のライセンス認証の利用、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  開く間にあるすべてを置換\<ウィンドウ > タグと終了\</Window > タグで、次マークアップでします。  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>アニメーションを使用します。  
 楽しい、グラデーション ブラシの色をアニメーション化してみましょう。 次の追加[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、終了後に`</InkCanvas>`タグが終了する前に`</Page>`タグ。  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>XAML の背後にある一部のコードを追加します。  
 XAML では、非常に簡単にユーザー インターフェイスをデザイン、イベントを処理するコードを追加する任意の実際のアプリケーションが必要です。 右クリック マウスからの応答でインクを拡大する簡単な例を次に示します。  
  
 設定、`MouseRightButtonUp`ハンドラー、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 Visual Studio のソリューション エクスプ ローラーで、Windows1.xaml を展開し、window1.xaml.cs の名前または Window1.xaml.vb Visual Basic を使用している場合、分離コード ファイルを開きます。 次のイベント ハンドラーのコードを追加します。  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 ここで、アプリケーションを実行します。 インクを追加およびマウスで右クリックするか、スタイラスを使用して、等価なプレス アンド ホールドを実行します。  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>XAML ではなく、手続き型コードを使用します。  
 すべてにアクセスできる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]手続き型コードから機能します。 ここでは、"こんにちはインク World"アプリケーションの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用しない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]まったくです。 Visual Studio での空のコンソール アプリケーションには、次のコードを貼り付けます。 PresentationCore、PresentationFramework、および WindowsBase アセンブリへの参照を追加し、キーを押してアプリケーションをビルド**f5 キーを押して**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>参照  
 [デジタル インク](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [インクの収集](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [手書き認識](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [インクの格納](../../../../docs/framework/wpf/advanced/storing-ink.md)
