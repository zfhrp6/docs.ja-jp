---
title: "スタイラスからの入力のインターセプト | Microsoft Docs"
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
  - "アーキテクチャ, System.Windows.Input.StylusPlugIns"
  - "InkCanvas, 追加 (プラグインを)"
  - "プラグイン, スタイラス"
  - "StylusPlugIns アーキテクチャ"
  - "System.Windows.Input.StylusPlugIns アーキテクチャ"
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# スタイラスからの入力のインターセプト
<xref:System.Windows.Input.StylusPlugIns> アーキテクチャは、<xref:System.Windows.Input.Stylus> 入力およびデジタル インクの <xref:System.Windows.Ink.Stroke> オブジェクトの作成に対する低レベルの制御を実装するための機構です。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> クラスは、カスタム動作を実装し、その動作をスタイラス デバイスから取得されるデータのストリームに適用するための機構で、最高のパフォーマンスを実現するように作られています。  
  
 このトピックは、次の内容で構成されています。  
  
-   [アーキテクチャ](#Architecture)  
  
-   [スタイラス プラグインを実装する](#ImplementingStylusPlugins)  
  
-   [InkCanvas にプラグインを追加する](#AddingYourPluginToAnInkCanvas)  
  
-   [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## アーキテクチャ  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> は、[StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) の API を発展させたものです。この API については、「[Microsoft Windows XP Tablet PC Edition Software Development Kit 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)」の「[Accessing and Manipulating Pen Input](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)」を参照してください。  
  
 各 <xref:System.Windows.UIElement> には、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> である <xref:System.Windows.UIElement.StylusPlugIns%2A> プロパティがあります。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> を要素の <xref:System.Windows.UIElement.StylusPlugIns%2A> プロパティに追加することにより、<xref:System.Windows.Input.StylusPoint> データをその生成時に操作できます。  <xref:System.Windows.Input.StylusPoint> データは、<xref:System.Windows.Input.StylusPoint.X%2A> および <xref:System.Windows.Input.StylusPoint.Y%2A> のポイント データや <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> データなどの、システム デジタイザーでサポートされるすべてのプロパティから構成されます。  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> を <xref:System.Windows.UIElement.StylusPlugIns%2A> プロパティに追加すると、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> オブジェクトは <xref:System.Windows.Input.Stylus> デバイスから取得されるデータのストリームに直接挿入されます。  プラグインを <xref:System.Windows.UIElement.StylusPlugIns%2A> コレクションに追加する順序によって、プラグインが <xref:System.Windows.Input.StylusPoint> データを受信する順序が決まります。  たとえば、入力を特定の領域に制限するフィルター プラグインを追加した後に、書き込まれるジェスチャを認識するプラグインを追加した場合は、ジェスチャを認識するプラグインが受け取るデータは既にフィルター処理された <xref:System.Windows.Input.StylusPoint> データです。  
  
<a name="ImplementingStylusPlugins"></a>   
## スタイラス プラグインを実装する  
 プラグインを実装するには、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> の派生クラスを作成します。  このクラスは、<xref:System.Windows.Input.Stylus> からのデータのストリームに適用されます。  このクラスの中で、<xref:System.Windows.Input.StylusPoint> データの値を変更できます。  
  
> [!CAUTION]
>  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> が例外をスローまたは発生させた場合、アプリケーションは終了します。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> を使用するコントロールを十分にテストし、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> が例外をスローしないことが確実な場合だけ、コントロールを使用するようにしてください。  
  
 <xref:System.Windows.Input.Stylus> デバイスから受け取る <xref:System.Windows.Input.StylusPoint> データの <xref:System.Windows.Input.StylusPoint.X%2A> と <xref:System.Windows.Input.StylusPoint.Y%2A> の値を変更することでスタイラス入力を制限するプラグインの例を次に示します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## InkCanvas にプラグインを追加する  
 カスタム プラグインを使用するための最も簡単方法は、InkCanvas から派生するクラスを実装し、<xref:System.Windows.UIElement.StylusPlugIns%2A> プロパティに追加することです。  
  
 インクをフィルター処理するカスタム <xref:System.Windows.Controls.InkCanvas> の例を次に示します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 `FilterInkCanvas` をアプリケーションに追加して実行すると、ユーザーがストロークを完了するまでインクは一定の領域に制限されないことがわかります。  これは、<xref:System.Windows.Controls.InkCanvas> には <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> プロパティがあり、このプロパティは <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> で、既に <xref:System.Windows.UIElement.StylusPlugIns%2A> コレクションのメンバーであるためです。  <xref:System.Windows.UIElement.StylusPlugIns%2A> コレクションに追加したカスタム <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> は、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> が <xref:System.Windows.Input.StylusPoint> データを受信した後に、そのデータを受信します。  その結果、<xref:System.Windows.Input.StylusPoint> データがフィルター処理されるのは、ユーザーがペンを持ち上げてストロークを完了したときとなります。  ユーザーがインクを描画した時点でインクをフィルター処理するには、`FilterPlugin` を <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> の前に挿入する必要があります。  
  
 次の C\# コードは、インク描画時にフィルター処理するカスタム <xref:System.Windows.Controls.InkCanvas> を示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## まとめ  
 独自の <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> クラスを派生させて <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> コレクションに挿入することで、デジタル インクの動作を大幅に向上させることができます。  <xref:System.Windows.Input.StylusPoint> データが生成された時点でアクセスできるので、<xref:System.Windows.Input.Stylus> 入力をカスタマイズできるようになります。  このような、低レベルでの <xref:System.Windows.Input.StylusPoint> データへのアクセスが可能であることから、アプリケーションでのインク収集およびレンダリングの実装のパフォーマンスが最大になります。  
  
## 参照  
 [高度なインク処理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)   
 [Accessing and Manipulating Pen Input \(ペン入力のアクセスと操作\)](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)