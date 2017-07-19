---
title: "インク スレッド モデル | Microsoft Docs"
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
  - "アプリケーション ユーザー インターフェイス スレッド"
  - "動的レンダリング スレッド"
  - "インク コレクション プラグイン"
  - "インク スレッド モデル"
  - "インク, 描画"
  - "ペン スレッド"
  - "プラグイン, インク"
  - "レンダリング インク"
  - "スタイラス プラグイン"
  - "スレッド化モデル"
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# インク スレッド モデル
Tablet PC でインクを使用することの利点の 1 つは、通常のペンと用紙を使用して書いている感覚に非常に近いことです。  これを実現するために、タブレット ペンはマウスよりも非常に高いレートで入力データを収集し、ユーザーが書いたとおりにインクを描画します。  アプリケーションのユーザー インターフェイス \(UI\) スレッドは、ブロックされる可能性があるため、ペンのデータを収集し、インクを描画するためには十分ではありません。  これを解決するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、ユーザーがインクを書く際に、2 つの追加スレッドを使用します。  
  
 デジタル インクの収集および描画に関与するスレッドを次のリストに示します。  
  
-   ペン スレッド \- スタイラスから入力を取得するスレッド   \(これは実際にはスレッド プールですが、ここではペン スレッドと呼びます\)。  
  
-   アプリケーション ユーザー インターフェイス スレッド \- アプリケーションのユーザー インターフェイスを制御するスレッド。  
  
-   動的レンダリング スレッド \- ユーザーがストロークを描画している間にインクを描画するスレッド。  動的レンダリング スレッドは、アプリケーションの他の UI 要素を描画するスレッドとは別のものです。詳細については、Window Presentation Foundation の「[スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)」を参照してください。  
  
 インク モデルは、アプリケーションが <xref:System.Windows.Controls.InkCanvas> を使用している場合でも、「[インク入力コントロールの作成](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)」で示したようなカスタム コントロールを使用している場合でも同じです。  ここでは、<xref:System.Windows.Controls.InkCanvas> でのスレッドについて説明していますが、カスタム コントロールを作成する場合でも、同じ概念が当てはまります。  
  
## スレッド処理の概要  
 ユーザーがストロークを描画する場合のスレッド モデルを次の図に示します。  
  
 ![ストローク描画中のスレッド処理モデル。](../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading\_DrawingInk")  
  
1.  ユーザーがストロークを描画している間に発生するアクション  
  
    1.  ユーザーがストロークを描画すると、スタイラス ポイントはペン スレッドに入ります。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> などのスタイラス プラグインは、ペン スレッドでスタイラス ポイントを受け入れ、<xref:System.Windows.Controls.InkCanvas> が受け取る前にそれらのポイントを変更することができます。  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> が、動的レンダリング スレッドでスタイラス ポイントを描画します。  これは、前の手順と同時に行われます。  
  
    3.  <xref:System.Windows.Controls.InkCanvas> が、UI スレッドでスタイラス ポイントを受け取ります。  
  
2.  ユーザーがストロークを終了した後に発生するアクション  
  
    1.  ユーザーがストロークの描画を終了すると、<xref:System.Windows.Controls.InkCanvas> が <xref:System.Windows.Ink.Stroke> オブジェクトを作成し、それを静的に描画する <xref:System.Windows.Controls.InkPresenter> に追加します。  
  
    2.  UI スレッドはストロークが静的に描画されることを <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> に通知し、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> はストロークの視覚的表現を削除します。  
  
## インク コレクションとスタイラス プラグイン  
 各 <xref:System.Windows.UIElement> には、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> があります。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> の <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> オブジェクトは、ペン スレッドでスタイラス ポイントを受け取り、それを変更することができます。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> オブジェクトは、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> での順序に従って、スタイラス ポイントを受け取ります。  
  
 <xref:System.Windows.UIElement> の <xref:System.Windows.UIElement.StylusPlugIns%2A> コレクションに、`stylusPlugin1`、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、および `stylusPlugin2` がこの順序で含まれていると仮定した場合の状況を次の図に示します。  
  
 ![スタイラス プラグインの順序は出力に影響します。](../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading\_PluginOrder")  
  
 この図では、次の動作が実行されます。  
  
1.  `StylusPlugin1` が、x と y の値を変更します。  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> が、変更されたスタイラス ポイントを受け取り、それらを動的レンダリング スレッドで描画します。  
  
3.  `StylusPlugin2` が、変更されたスタイラス ポイントを受け取り、x と y の値をさらに変更します。  
  
4.  アプリケーションはスタイラス ポイントを収集し、ユーザーがストロークを終了すると、ストロークを静的に描画します。  
  
 `stylusPlugin1` がスタイラス ポイントを四角形に制限し、`stylusPlugin2` がスタイラス ポイントを右に平行移動するとします。  前のシナリオでは、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> は制限されたスタイラス ポイントを受け取りますが、平行移動されたスタイラス ポイントは受け取りません。  ユーザーがストロークを描画すると、そのストロークは四角形の境界内に描画されますが、ユーザーがペンを持ち上げるまで平行移動されません。  
  
### UI スレッドでスタイラス プラグインを使用した操作を実行する  
 ペン スレッドでは正確なヒット テストを実行できないため、場合によっては、一部の要素が他の要素を対象としたスタイラス入力を受け取ることがあります。  操作を実行する前に、入力が正しくルーティングされていることを確認する必要がある場合は、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>、または <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> の各メソッドにサブスクライブし、そのメソッド内で操作を実行します。  これらのメソッドは、正確なヒット テストが実行された後に、アプリケーション スレッドによって呼び出されます。  これらのメソッドにサブスクライブするには、ペン スレッドで実行されるメソッド内で <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> メソッドを呼び出します。  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> のスタイラス イベントに関連した、ペン スレッドと UI スレッドの関係を次の図に示します。  
  
 ![インク スレッド処理モデル &#40;UI およびペン&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading\_PluginCallbacks")  
  
## インクのレンダリング  
 ユーザーがストロークを描画すると、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> はインクを別スレッドで描画するため、UI スレッドがビジー状態であっても、インクはペンから "流れ出る" ように見えます。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> は、スタイラス ポイントを収集しながら、動的レンダリング スレッドでビジュアル ツリーを構築します。  ユーザーがストロークを終了すると、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> は、アプリケーションが次の描画パスを実行する際に通知するように要求します。  アプリケーションが次の描画パスを完了した後、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> はビジュアル ツリーをクリーンアップします。  このプロセスを説明する図を次に示します。  
  
 ![インク スレッド処理のダイアグラム](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading\_VisualTree")  
  
1.  ユーザーがストロークを開始したとき。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> がビジュアル ツリーを作成します。  
  
2.  ユーザーがストロークを描画している間。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> がビジュアル ツリーを構築します。  
  
3.  ユーザーがストロークを終了したとき。  
  
    1.  <xref:System.Windows.Controls.InkPresenter> がストロークを自分のビジュアル ツリーに追加します。  
  
    2.  メディア統合レイヤー \(MIL\) がストロークを静的に描画します。  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> がビジュアルをクリーンアップします。