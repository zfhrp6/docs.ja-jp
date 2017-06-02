---
title: "方法 : CompositionTarget を使用したフレームの間隔ごとの描画 | Microsoft Docs"
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
  - "CompositionTarget オブジェクト, 描画 (フレームごとに)"
  - "描画 (CompositionTarget オブジェクトを使用してフレームごとに)"
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : CompositionTarget を使用したフレームの間隔ごとの描画
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、フレームベースのアニメーションを作成するためのさまざまな機能が用意されています。  ただし、フレームベースの描画をさらにきめ細かく制御することが必要となるアプリケーション シナリオがあります。  <xref:System.Windows.Media.CompositionTarget> オブジェクトを使用すると、フレームごとのコールバックに基づいてカスタム アニメーションを作成できます。  
  
 <xref:System.Windows.Media.CompositionTarget> は、アプリケーションが描画される表示サーフェイスを表す静的クラスです。  アプリケーションのシーンが描画されるたびに <xref:System.Windows.Media.CompositionTarget.Rendering> イベントが発生します。  レンダリング フレーム レートは、1 秒あたりのシーンの描画回数です。  
  
> [!NOTE]
>  <xref:System.Windows.Media.CompositionTarget> を使用したコード サンプル全体については、「[Using the CompositionTarget Sample \(CompositionTarget のサンプルの使用\)](http://go.microsoft.com/fwlink/?LinkID=160045)」を参照してください。  
  
## 使用例  
 <xref:System.Windows.Media.CompositionTarget.Rendering> イベントは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の描画プロセス中に発生します。  静的 <xref:System.Windows.Media.CompositionTarget.Rendering> メソッドに対する <xref:System.EventHandler> デリゲートを <xref:System.Windows.Media.CompositionTarget> に登録する方法を次の例に示します。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 独自の描画イベント ハンドラー メソッドを使用して、描画のカスタム コンテンツを作成できます。  このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が[ビジュアル ツリー](GTMT)の永続化されたレンダリング データを合成シーン グラフにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  さらに、[ビジュアル ツリー](GTMT)に対する変更によって合成シーン グラフが強制的に更新される場合も、イベント ハンドラー メソッドが呼び出されます。  イベント ハンドラー メソッドは、レイアウトが計算された後に呼び出されます。  ただし、イベント ハンドラー メソッド内でレイアウトを変更できます。つまり、そのレイアウトは、描画する前にもう一度計算されることになります。  
  
 <xref:System.Windows.Media.CompositionTarget> イベント ハンドラー メソッドでカスタム描画を指定する方法を次の例に示します。  この場合、<xref:System.Windows.Controls.Canvas> の背景色は、マウスの座標位置に基づくカラー値で描画されます。  <xref:System.Windows.Controls.Canvas> 内でマウスを移動すると、その背景色が変わります。  また、現在の経過時間および描画されたフレームの合計数に基づいて、平均フレーム レートが計算されます。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 カスタム描画は、コンピューターごとに異なる速度で実行される場合があります。  これは、カスタム描画がフレーム レートに依存するためです。  実行しているシステムとそのシステムの負荷に応じて、<xref:System.Windows.Media.CompositionTarget.Rendering> イベントが 1 秒あたりに呼び出される回数が異なる場合があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを実行するデバイスのグラフィックス ハードウェアの機能およびパフォーマンスの決定については、「[グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)」を参照してください。  
  
 イベントの発生中の描画 <xref:System.EventHandler> デリゲートの追加または削除は、イベントが終了するまで遅延します。  これは、<xref:System.MulticastDelegate> ベースのイベントが共通言語ランタイム \(CLR\) で処理される方法と一貫性があります。  また、描画イベントが特定の順序で呼び出されるかどうかは保証されません。  特定の順序に依存する複数の <xref:System.EventHandler> デリゲートがある場合、単一の <xref:System.Windows.Media.CompositionTarget.Rendering> イベントを登録し、手動でデリゲートを正しい順序で多重化する必要があります。  
  
## 参照  
 <xref:System.Windows.Media.CompositionTarget>   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)