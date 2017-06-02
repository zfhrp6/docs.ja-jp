---
title: "チュートリアル: 初めてのタッチ アプリケーションの作成 | Microsoft Docs"
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
  - "作成 (タッチスクリーン アプリケーションを) [WPF]"
  - "作成 (タッチを検知するアプリケーションを) [WPF]"
  - "タッチスクリーン アプリケーション [WPF], 作成"
  - "タッチを検知するアプリケーション [WPF], 作成"
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# チュートリアル: 初めてのタッチ アプリケーションの作成
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、タッチに応答するアプリケーションを作成できます。  たとえば、タッチスクリーンなどのタッチを検知するデバイスで 1 本または複数本の指を使用してアプリケーションを操作できます。このチュートリアルでは、タッチすることで単一のオブジェクトを移動、サイズ変更または回転させることのできるアプリケーションを作成します。  
  
## 必要条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7。  
  
-   Windows タッチをサポートする、タッチスクリーンなどのタッチ入力ができるデバイス。  
  
 また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのアプリケーションの作成において、特にイベントのサブスクライブ方法と処理方法に関する基礎知識があることが必要です。  詳細については、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。  
  
## アプリケーションの作成  
  
#### アプリケーションを作成するには  
  
1.  Visual Basic または Visual C\# で、「`BasicManipulation`」という名前の新しい WPF アプリケーション プロジェクトを作成します。  詳細については、「[方法 : 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)」を参照してください。  
  
2.  MainWindow.xaml の内容を次の XAML に置き換えます。  
  
     マークアップにより、<xref:System.Windows.Controls.Canvas> 上に赤い <xref:System.Windows.Shapes.Rectangle> を含む単純なアプリケーションが作成されます。  <xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.UIElement.IsManipulationEnabled%2A> プロパティは、操作イベントを受け取ることができるように true に設定されます。  アプリケーションは、<xref:System.Windows.UIElement.ManipulationStarting> イベント、<xref:System.Windows.UIElement.ManipulationDelta> イベントおよび <xref:System.Windows.UIElement.ManipulationInertiaStarting> イベントをサブスクライブします。  これらのイベントには、ユーザーが操作したときに <xref:System.Windows.Shapes.Rectangle> を移動するためのロジックが含まれています。  
  
     [!code-xml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Visual Basic を使用している場合は、MainWindow.xaml の最初の行で、`x:Class="BasicManipulation.MainWindow"` を `x:Class="MainWindow"` で置換します。  
  
4.  `MainWindow` クラスに、次の <xref:System.Windows.UIElement.ManipulationStarting> イベント ハンドラーを追加します。  
  
     <xref:System.Windows.UIElement.ManipulationStarting> イベントは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がタッチ入力によるオブジェクト操作の開始を検知すると発生します。  コードでは、<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> プロパティを設定することで、操作の位置が <xref:System.Windows.Window> と相対するように指定します。  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  `MainWindow` クラスに、次の <xref:System.Windows.Input.ManipulationDelta> イベント ハンドラーを追加します。  
  
     <xref:System.Windows.Input.ManipulationDelta> イベントは、タッチ入力の位置が変更されると発生し、一度の操作中に複数回発生することがあります。  イベントは、指を離した後にも発生します。  たとえば、ユーザーが画面上で指をドラッグすると、<xref:System.Windows.Input.ManipulationDelta> イベントは指が移動するたびに複数回発生します。  ユーザーが指を画面から離すと、<xref:System.Windows.Input.ManipulationDelta> イベントは慣性をシミュレートするために発生し続けます。  
  
     コードでは、ユーザーのタッチ入力に沿って移動するために、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.UIElement.RenderTransform%2A> に <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> を適用します。  また、慣性処理中にイベントが発生したときに、<xref:System.Windows.Shapes.Rectangle> が <xref:System.Windows.Window> の境界の外側にあるかどうかもチェックします。  境界の外側にある場合、アプリケーションは <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=fullName> メソッドを呼び出して操作を終了します。  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  `MainWindow` クラスに、次の <xref:System.Windows.UIElement.ManipulationInertiaStarting> イベント ハンドラーを追加します。  
  
     ユーザーが画面からすべての指を離すと、<xref:System.Windows.UIElement.ManipulationInertiaStarting> イベントが発生します。  コードにより、四角形の移動、拡大および回転に対する初期の速度と減速度が設定されます。  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  プロジェクトをビルドして実行します。  
  
     ウィンドウ内に赤い正方形が表示されます。  
  
## アプリケーションのテスト  
 アプリケーションをテストするには、次の操作を試します。  一度に複数の操作を試すことができます。  
  
-   <xref:System.Windows.Shapes.Rectangle> を移動するには、<xref:System.Windows.Shapes.Rectangle> の上に 1 本の指を置き、画面上でその指を動かします。  
  
-   <xref:System.Windows.Shapes.Rectangle> のサイズを変更するには、<xref:System.Windows.Shapes.Rectangle> 上に 2 本の指を置き、指どうしの距離を互いに近づけるか離します。  
  
-   <xref:System.Windows.Shapes.Rectangle> を回転させるには、<xref:System.Windows.Shapes.Rectangle> 上に 2 本の指を置き、互いの周りで指を回します。  
  
 慣性を発生させるには、直前の操作を実行したときに画面からすばやく指を離します。  <xref:System.Windows.Shapes.Rectangle> は、停止するまでの数秒間、移動、サイズ変更または回転を続けます。  
  
## 参照  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=fullName>   
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=fullName>   
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=fullName>