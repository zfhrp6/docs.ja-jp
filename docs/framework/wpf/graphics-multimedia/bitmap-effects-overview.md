---
title: "ビットマップ効果の概要 | Microsoft Docs"
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
  - "ビットマップ効果"
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# ビットマップ効果の概要
ビットマップ効果により、デザイナーおよび開発者は、描画された [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] コンテンツに視覚効果を適用できます。  たとえば、ビットマップ効果を使用すると、イメージまたはボタンに <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 効果やぼかし効果を簡単に適用できます。  
  
> [!IMPORTANT]
>  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降では、<xref:System.Windows.Media.Effects.BitmapEffect> クラスは使用されなくなりました。  <xref:System.Windows.Media.Effects.BitmapEffect> クラスを使用すると、廃止されていることを示す例外が返されます。  <xref:System.Windows.Media.Effects.BitmapEffect> クラスの代替としては <xref:System.Windows.Media.Effects.Effect> クラスを使用できます。  ほとんどの場合は、<xref:System.Windows.Media.Effects.Effect> クラスを使用した方が高速に処理できます。  
  
   
  
<a name="wpf_effects"></a>   
## WPF ビットマップ効果  
 ビットマップ効果 \(<xref:System.Windows.Media.Effects.BitmapEffect> オブジェクト\) は、単純なピクセル処理操作です。  ビットマップ効果は入力として <xref:System.Windows.Media.Imaging.BitmapSource> を取得し、ぼかしやドロップ シャドウなどの効果を適用した後で、新しい <xref:System.Windows.Media.Imaging.BitmapSource> を生成します。  各ビットマップ効果は、フィルタリング プロパティを制御できるプロパティ \(<xref:System.Windows.Media.Effects.BlurBitmapEffect> の <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> など\) を公開します。  
  
 特殊なケースとして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、<xref:System.Windows.Controls.Button> や <xref:System.Windows.Controls.TextBox> などの使用中の <xref:System.Windows.Media.Visual> オブジェクトのプロパティとして効果を設定できます。  ピクセル処理が適用され、実行時に描画されます。  この場合、描画時に、<xref:System.Windows.Media.Visual> は等価の <xref:System.Windows.Media.Imaging.BitmapSource> に自動的に変換され、<xref:System.Windows.Media.Effects.BitmapEffect> の入力として供給されます。  出力により、<xref:System.Windows.Media.Visual> オブジェクトの既定のレンダリング動作が置き換えられます。  そのため、<xref:System.Windows.Media.Effects.BitmapEffect> オブジェクトはビジュアルがソフトウェアのみで描画されることを強制します。つまり、  効果の適用時には、ビジュアルに対してハードウェア アクセラレータは使用されません。  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> は、焦点を外したように見えるオブジェクトをシミュレートします。  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> は、オブジェクトの周囲に色のにじみを作成します。  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> は、オブジェクトの背後に影を作成します。  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> は、指定した曲線に従ってイメージの表面を浮き上がらせる傾斜面を作成します。  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> は <xref:System.Windows.Media.Visual> のバンプ マッピングを作成し、人工光源による奥行とテクスチャから得られる印象を生成します。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ビットマップ効果は、ソフトウェア モードで描画されます。  効果を適用するすべてのオブジェクトもソフトウェアで描画されます。  パフォーマンスが最も低下するのは、ビットマップ効果を大規模なビジュアルやビットマップ効果のアニメーション プロパティに適用した場合です。  ビットマップ効果をこのような方法で使用してはならないわけではありませんが、予期したとおりのエクスペリエンスをユーザーが体験することを保証するため、使用する場合は細心の注意を払い、徹底的にテストしてください。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ビットマップ効果は、部分信頼では実行できません。  アプリケーションでビットマップ効果を使用するには、完全信頼のアクセス許可が必要です。  
  
<a name="applyeffects"></a>   
## 効果を適用する方法  
 <xref:System.Windows.Media.Effects.BitmapEffect> は <xref:System.Windows.Media.Visual> のプロパティです。  したがって、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Image>、<xref:System.Windows.Media.DrawingVisual>、<xref:System.Windows.UIElement> などのビジュアルに効果を適用するのは、プロパティを設定するのと同様に簡単です。  <xref:System.Windows.UIElement.BitmapEffect%2A> は 1 つの <xref:System.Windows.Media.Effects.BitmapEffect> オブジェクトに設定できます。また、<xref:System.Windows.Media.Effects.BitmapEffectGroup> オブジェクトを使用して、複数の効果を連結することもできます。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で <xref:System.Windows.Media.Effects.BitmapEffect> を適用する方法を次の例に示します。  
  
 [!code-xml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 コードで <xref:System.Windows.Media.Effects.BitmapEffect> を適用する方法を次の例に示します。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.BitmapEffect> が <xref:System.Windows.Controls.DockPanel> や <xref:System.Windows.Controls.Canvas> などのレイアウト コンテナーに適用されると、効果は要素またはビジュアルのビジュアル ツリー \(すべての子要素を含む\) に適用されます。  
  
<a name="customeffects"></a>   
## カスタム効果の作成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、マネージ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで使用できるカスタム効果を作成するために、アンマネージ インターフェイスも提供します。  カスタム ビットマップ効果の作成に関する追加リファレンス資料については、「[アンマネージ WPF ビットマップ効果](_wibe_lh)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>   
 <xref:System.Windows.Media.Effects.BitmapEffectInput>   
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>   
 [Unmanaged WPF Bitmap Effect](_wibe_lh)   
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [セキュリティ](../../../../docs/framework/wpf/security-wpf.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)