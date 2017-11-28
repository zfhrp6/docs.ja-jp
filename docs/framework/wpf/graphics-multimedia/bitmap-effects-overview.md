---
title: "ビットマップ効果の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76b767fd210deed536b4452dc6d7bb505f5bd3e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bitmap-effects-overview"></a>ビットマップ効果の概要
ビットマップ効果を使うと、設計者と開発者は、レンダリングされる [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] コンテンツに視覚効果を適用できます。 たとえば、ビットマップ効果を簡単に適用できます、<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>特殊効果またはイメージやボタンをぼかし効果。  
  
> [!IMPORTANT]
>  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]以降、<xref:System.Windows.Media.Effects.BitmapEffect>クラスが廃止されています。 使用しようとする場合、<xref:System.Windows.Media.Effects.BitmapEffect>クラス、古い形式の例外が表示されます。 旧式でない代わりに、<xref:System.Windows.Media.Effects.BitmapEffect>クラスは、<xref:System.Windows.Media.Effects.Effect>クラスです。 ほとんどの場合、<xref:System.Windows.Media.Effects.Effect>クラスは大幅に高速です。  
  
  
  
<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF のビットマップ効果  
 ビットマップ効果 (<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクト) 処理操作は、単純なピクセルです。 ビットマップ効果の方が、<xref:System.Windows.Media.Imaging.BitmapSource>として、入力、新規生成<xref:System.Windows.Media.Imaging.BitmapSource>ぼかしまたはドロップ シャドウなどの効果を適用した後にします。 各ビットマップ効果など、フィルター処理のプロパティを制御できるプロパティを公開する<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>の<xref:System.Windows.Media.Effects.BlurBitmapEffect>します。  
  
 特殊なケースとしてに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、効果に対して設定できるプロパティとしてライブ<xref:System.Windows.Media.Visual>などのオブジェクト、<xref:System.Windows.Controls.Button>または<xref:System.Windows.Controls.TextBox>です。 ピクセル処理は、実行時に適用されてレンダリングされます。 、レンダリング時にこの例では、、<xref:System.Windows.Media.Visual>に自動的に変換がその<xref:System.Windows.Media.Imaging.BitmapSource>等価への入力として渡すと、<xref:System.Windows.Media.Effects.BitmapEffect>です。 出力の置換、<xref:System.Windows.Media.Visual>オブジェクトの既定のレンダリング動作します。 その理由は<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクトが効果を適用するときに、ビジュアルにハードウェア アクセラレータのみつまりなしをソフトウェアに表示するビジュアルを強制します。  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect>焦点の外に表示されるオブジェクトをシミュレートします。  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>オブジェクトの周囲の色の付いた光輪を作成します。  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>オブジェクトの内側に影が付きます。  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect>指定した曲線に従ってイメージの表面を浮き上がらせるベベルを作成します。  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect>バンプ マッピングを作成、<xref:System.Windows.Media.Visual>人工光源から奥行きとテクスチャの印象にします。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のビットマップ効果は、ソフトウェア モードでレンダリングされます。 効果を適用するオブジェクトも、ソフトウェアでレンダリングされます。 大きなビジュアルにビットマップ効果を使うとき、またはビットマップ効果のプロパティをアニメーション化するときに、パフォーマンスが最も低下します。 このような方法ではビットマップ効果をまったく使ってはならないということではありませんが、注意を払い、十分にテストを行って、ユーザー エクスペリエンスが期待どおりになることを確認する必要があります。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のビットマップ効果は、部分信頼の実行をサポートしていません。 ビットマップ効果を使うには、アプリケーションが完全な信頼のアクセス許可を持つ必要があります。  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>効果を適用する方法  
 <xref:System.Windows.Media.Effects.BitmapEffect>プロパティは、<xref:System.Windows.Media.Visual>です。 このためなどをビジュアルに、その効果を適用する、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.Image>、 <xref:System.Windows.Media.DrawingVisual>、または<xref:System.Windows.UIElement>プロパティの設定と同じくらい簡単です。 <xref:System.Windows.UIElement.BitmapEffect%2A>1 つに設定することができます<xref:System.Windows.Media.Effects.BitmapEffect>を使用してオブジェクトまたは複数の効果をチェーンできる、<xref:System.Windows.Media.Effects.BitmapEffectGroup>オブジェクト。  
  
 次の例では、適用する方法、<xref:System.Windows.Media.Effects.BitmapEffect>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 次の例では、適用する方法、<xref:System.Windows.Media.Effects.BitmapEffect>のコードにします。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  ときに、<xref:System.Windows.Media.Effects.BitmapEffect>などで、レイアウト コンテナーに適用される<xref:System.Windows.Controls.DockPanel>または<xref:System.Windows.Controls.Canvas>、要素またはビジュアルを含むすべての子要素のビジュアル ツリーに効果を適用します。  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>カスタム効果の作成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、マネージ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで使うことができるカスタム効果を作成するためのアンマネージ インターフェイスも提供されています。 カスタム ビットマップ効果の作成に関する参考資料については、「[Unmanaged WPF Bitmap Effect](https://msdn.microsoft.com/library/ms735092.aspx)」(アンマネージ WPF ビットマップ効果) ドキュメントをご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>  
 <xref:System.Windows.Media.Effects.BitmapEffectInput>  
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>  
 [アンマネージ WPF ビットマップ効果](https://msdn.microsoft.com/library/ms735092.aspx)  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [セキュリティ](../../../../docs/framework/wpf/security-wpf.md)  
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
