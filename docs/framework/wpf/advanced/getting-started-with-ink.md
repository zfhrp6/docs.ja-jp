---
title: "インクの概要 | Microsoft Docs"
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
  - "アニメーション, グラデーション ブラシの色"
  - "ブラシ, アニメーション化 (色を)"
  - "グラデーション ブラシ, アニメーション化 (色を)"
  - "XAML の代わりに手続き型コードを使用"
  - "XAML, 代わりに手続き型コードを使用"
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# インクの概要
アプリケーションへのデジタル インクの組み込みは、今までになく容易になりました。  COM および Windows フォームによるプログラミング手法の付随的な存在であったインクは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に完全に統合されるまでに発展しました。  個別の SDK や、ランタイム ライブラリをインストールする必要はありません。  
  
## 必要条件  
 以降に示す例を使用するには、まず Microsoft Visual Studio 2005 および [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] をインストールする必要があります。  また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対応するアプリケーションの作成方法も理解しておく必要があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の概要については、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。  
  
## クイック スタート  
 ここでは、インクを収集する簡単な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを作成する方法を説明します。  
  
 Microsoft Visual Studio 2005 および [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] をまだインストールしていない場合はインストールしてください。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを表示するには、その全体が [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で構成されている場合でも、通常はあらかじめコンパイルしておく必要があります。  また、[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] には、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ベースの UI の実装作業を迅速化するために設計された、XamlPad というアプリケーションが付属しています。  このアプリケーションを使用して、このドキュメントの最初にあるいくつかのサンプルを表示し、いろいろと変更してみるとよいでしょう。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] からコンパイルされたアプリケーションを作成する作業については、このドキュメントで後に説明します。  
  
 XAMLPad を起動するには、\[スタート\] ボタンをクリックし、\[すべてのプログラム\] をポイントします。次に、\[Microsoft Windows SDK\] をポイントし、\[Tools\] をポイントして、\[XAMLPad\] をクリックします。  XAMLPad のレンダリング ペインには、コード ペインで作成された XAML コードがレンダリングされます。  XAML コードを編集すると、変更は直ちにレンダリング ペインに反映されます。  
  
#### インクを取得する  
 インクをサポートする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを初めて作成するには、次の手順を実行します。  
  
1.  Microsoft Visual Studio 2005 を開きます。  
  
2.  新しい Windows アプリケーション \(WPF\) を作成します。  
  
3.  2 つの `<Grid>` タグの間に「`<InkCanvas/>`」と入力します。  
  
4.  デバッガーでアプリケーションを起動するために、**F5** キーを押します。  
  
5.  スタイラスまたはマウスを使用して、ウィンドウに「hello world」と書き込みます。  
  
 "hello world" アプリケーションに相当するインクが、わずか 12 回のキーストロークで書き込まれました。  
  
#### アプリケーションを改良する  
 次に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のいくつかの機能を利用してみましょう。  開始タグ \<Window\> と終了タグ \<\/Window\> の間にあるすべてのコードを、次に示すマークアップで置き換えてください。インク サーフェイスに、グラデーション ブラシによる背景が表示されます。  
  
 [!code-xml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### アニメーションを使用する  
 今度は、グラデーション ブラシの色をアニメーション化してみましょう。  次に示す [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を、終了タグ `</InkCanvas>` と終了タグ `</Page>` の間に追加します。  
  
 [!code-xml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### XAML に分離コードを追加する  
 XAML を使用すると、ユーザー インターフェイスの設計は非常に簡単になりますが、実際のアプリケーションには、イベントを処理するコードを追加する必要があります。  マウスが右クリックされたときにインクを拡大表示する簡単な例を次に示します。  
  
 作成した [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の中で、次のように `MouseRightButtonUp` ハンドラーを設定します。  
  
 [!code-xml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 Visual Studio のソリューション エクスプローラーで Windows1.xaml を展開し、分離コード ファイル Window1.xaml.cs \(Visual Basic を使用している場合は Window1.xaml.vb\) を開きます。  次に示すイベント ハンドラー コードを追加します。  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 ここで、アプリケーションを実行します。  いくつかのインクを追加してから、マウスで右クリックするか、またはスタイラスを使用して同等の操作であるプレス アンド ホールドを実行します。  
  
#### XAML の代わりに手順コードを使用する  
 手順コードからは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のすべての機能にアクセスできます。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を一切使用しない [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の "Hello Ink World" アプリケーションを次に示します。  Visual Studio で、次に示すコードを空のコンソール アプリケーションに貼り付けます。  PresentationCore、PresentationFramework、および WindowsBase の各アセンブリへの参照を追加し、**F5** キーを押してアプリケーションをビルドします。  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## 参照  
 [デジタル インク](../../../../docs/framework/wpf/advanced/digital-ink.md)   
 [インクの収集](../../../../docs/framework/wpf/advanced/collecting-ink.md)   
 [手書き認識](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)   
 [インクの格納](../../../../docs/framework/wpf/advanced/storing-ink.md)