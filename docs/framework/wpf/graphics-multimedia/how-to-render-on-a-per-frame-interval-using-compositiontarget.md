---
title: "方法 : CompositionTarget を使用したフレームの間隔ごとの描画"
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
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb7e917c59f11ed78f8d44fa4b674d8d572f3623
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>方法 : CompositionTarget を使用したフレームの間隔ごとの描画
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のアニメーション エンジンには、フレームベースのアニメーションを作成するためのさまざまな機能が用意されています。 ただし、フレームベースの描画をさらにきめ細かく制御することが必要となるアプリケーション シナリオがあります。 <xref:System.Windows.Media.CompositionTarget>オブジェクトは、フレームごとのコールバックに基づくカスタム アニメーションを作成する機能を提供します。  
  
 <xref:System.Windows.Media.CompositionTarget>アプリケーションが描画される画面の表面を表す静的クラスです。 <xref:System.Windows.Media.CompositionTarget.Rendering>イベントはアプリケーションのシーンは描画たびに発生します。 レンダリング フレーム レートは、1 秒あたりのシーンの描画回数です。  
  
> [!NOTE]
>  完全なコード サンプルを使用して、<xref:System.Windows.Media.CompositionTarget>を参照してください[CompositionTarget サンプルを使用して](http://go.microsoft.com/fwlink/?LinkID=160045)です。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.CompositionTarget.Rendering>中にイベントが発生した、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レンダリング処理します。 次の例は、登録する方法を示しています、 <xref:System.EventHandler> 、静的なデリゲート<xref:System.Windows.Media.CompositionTarget.Rendering>メソッド<xref:System.Windows.Media.CompositionTarget>です。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 独自の描画イベント ハンドラー メソッドを使用して、描画のカスタム コンテンツを作成できます。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを合成シーン グラフにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。 さらに、ビジュアル ツリーに対する変更によって合成シーン グラフが強制的に更新される場合も、イベント ハンドラー メソッドが呼び出されます。 イベント ハンドラー メソッドは、レイアウトが計算された後に呼び出されます。 ただし、イベント ハンドラー メソッド内でレイアウトを変更できます。つまり、そのレイアウトは、描画する前にもう一度計算されることになります。  
  
 次の例はどのように使用できるカスタム描画、<xref:System.Windows.Media.CompositionTarget>イベント ハンドラー メソッドです。 この場合の背景色、<xref:System.Windows.Controls.Canvas>マウスの座標位置に基づく色の値で描画します。 内でマウスを移動する場合、 <xref:System.Windows.Controls.Canvas>、その背景の色を変更します。 また、現在の経過時間および描画されたフレームの合計数に基づいて、平均フレーム レートが計算されます。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 カスタム描画は、コンピューターごとに異なる速度で実行される場合があります。 これは、カスタム描画がフレーム レートに依存するためです。 実行しているシステムとそのシステムのワークロードに応じて、<xref:System.Windows.Media.CompositionTarget.Rendering>異なる回数 1 秒あたりのイベントを呼び出すことができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを実行するデバイスのグラフィックス ハードウェアの機能およびパフォーマンスの決定については、「[グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)」を参照してください。  
  
 追加または削除を表示する<xref:System.EventHandler>デリゲートがイベントを発生させるときに、イベントの終了後まで遅延されますを発生させます。 これは、方法と一致<xref:System.MulticastDelegate>-ベースのイベントは、共通言語ランタイム (CLR) を処理します。 また、描画イベントが特定の順序で呼び出されるかどうかは保証されません。 複数ある場合<xref:System.EventHandler>デリゲートを特定の順序に依存する、1 つを登録する必要があります<xref:System.Windows.Media.CompositionTarget.Rendering>イベントおよびマルチプレクシング正しい内のデリゲートでは、自分で注文します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.CompositionTarget>  
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
