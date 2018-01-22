---
title: "チュートリアル: 初めてのタッチ アプリケーションの作成"
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
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08f4004329d15b527a889cd7b437a7f18278fc79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-your-first-touch-application"></a>チュートリアル: 初めてのタッチ アプリケーションの作成
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]タッチに応答するアプリケーションを有効にします。 たとえば、1 つを使用して、アプリケーションと対話できます。 または多くを指でタッチ スクリーンがこのチュートリアルにより、ユーザーに移動するアプリケーションを作成するなどのタッチ依存型デバイスのサイズ変更、またはタッチを使用して、1 つのオブジェクトを回転します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]。  
  
-   Windows 7。  
  
-   Windows タッチをサポートするタッチ スクリーンなど、タッチ入力を受け付けるデバイス。  
  
 さらでアプリケーションを作成する方法の基本的な知識を持つ必要があります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にサブスクライブし、イベントを処理する方法に特にです。 詳細については、次を参照してください。[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。  
  
## <a name="creating-the-application"></a>アプリケーションの作成  
  
#### <a name="to-create-the-application"></a>アプリケーションを作成するには  
  
1.  Visual Basic または Visual c# のという名前の新しい WPF アプリケーション プロジェクトを作成する`BasicManipulation`です。 詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。  
  
2.  MainWindow.xaml の内容を次の XAML に置き換えます。  
  
     このマークアップを含む赤い簡単なアプリケーションを作成する<xref:System.Windows.Shapes.Rectangle>上、<xref:System.Windows.Controls.Canvas>です。 <xref:System.Windows.UIElement.IsManipulationEnabled%2A>のプロパティ、<xref:System.Windows.Shapes.Rectangle>操作イベントを受信するために true に設定されています。 サブスクライブするアプリケーション、 <xref:System.Windows.UIElement.ManipulationStarting>、 <xref:System.Windows.UIElement.ManipulationDelta>、および<xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント。 これらのイベントに移動するためのロジックが含まれて、<xref:System.Windows.Shapes.Rectangle>ユーザーからの操作をすることです。  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Visual Basic で MainWindow.xaml の最初の行を使用している場合は置き換えます`x:Class="BasicManipulation.MainWindow"`で`x:Class="MainWindow"`です。  
  
4.  `MainWindow`クラス、次の追加<xref:System.Windows.UIElement.ManipulationStarting>イベント ハンドラー。  
  
     <xref:System.Windows.UIElement.ManipulationStarting>イベントが発生したときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]そのタッチを検出したオブジェクトを操作する入力を開始します。 コードでは、操作の位置が基準にする必要がありますを指定します、<xref:System.Windows.Window>を設定して、<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>プロパティです。  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  `MainWindow`クラス、次の追加<xref:System.Windows.Input.ManipulationDelta>イベント ハンドラー。  
  
     <xref:System.Windows.Input.ManipulationDelta>イベント、タッチ入力の位置を変更および操作中に複数回発生する可能性がときに発生します。 イベントは、指が発生した後にも発生することができます。 たとえば、ユーザーが、画面上で指をドラッグする場合、<xref:System.Windows.Input.ManipulationDelta>イベントは、複数回を指移動するときに発生します。 ユーザーが画面で、指を発生させた、<xref:System.Windows.Input.ManipulationDelta>慣性をシミュレートするためにイベントが発生し続けます。  
  
     コードが適用されます、<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>を<xref:System.Windows.UIElement.RenderTransform%2A>の<xref:System.Windows.Shapes.Rectangle>ユーザーは、タッチを移動すると移動する入力します。 またを確認するかどうか、<xref:System.Windows.Shapes.Rectangle>の境界外または、<xref:System.Windows.Window>慣性中に、イベントの発生します。 そのため、アプリケーションを呼び出す場合、<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>メソッドを操作を終了します。  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  `MainWindow`クラス、次の追加<xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント ハンドラー。  
  
     <xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント、ユーザーが画面からのすべての指を発生させるときに発生します。 コードでは、初期速度と、移動、拡張、および四角形の回転の減速を設定します。  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  プロジェクトをビルドして実行します。  
  
     ウィンドウに表示される赤い四角形が表示されます。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 アプリケーションをテストするには、次の操作を再試行してください。 複数の次のいずれか、同時に実行できることに注意してください。  
  
-   移動する、 <xref:System.Windows.Shapes.Rectangle>、に指を置き、<xref:System.Windows.Shapes.Rectangle>し、画面上で指を移動します。  
  
-   サイズを変更する、 <xref:System.Windows.Shapes.Rectangle>、2 本の指の電源を入れます、<xref:System.Windows.Shapes.Rectangle>して近い一緒にまたは遠く互いとは別に、指を移動します。  
  
-   回転する、 <xref:System.Windows.Shapes.Rectangle>、2 本の指の電源を入れます、<xref:System.Windows.Shapes.Rectangle>指が互いの周りの回転とします。  
  
 慣性の直前の操作を実行するとは、指を画面からすばやくを発生させます。 <xref:System.Windows.Shapes.Rectangle>移動、サイズ変更、または停止する前に、数秒回転し続けます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
