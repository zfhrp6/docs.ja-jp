---
title: "方法 : 影付きテキストを作成する | Microsoft Docs"
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
  - "シャドウ効果 (テキストの)"
  - "テキスト, 'Shadows' を実行"
  - "タイポグラフィ, シャドウ効果"
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : 影付きテキストを作成する
このセクションの例では、表示テキストのシャドウ効果を作成する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Effects.DropShadowEffect> オブジェクトを使用すると、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] オブジェクトのさまざまなドロップ シャドウ効果を作成できます。  テキストにドロップ シャドウ効果が適用されている例を次に示します。  ここでは、影はソフト シャドウで、影の色にぼかしが使用されています。  
  
 ![ぼかし &#61; 0.25 のテキスト シャドウ](../../../../docs/framework/wpf/advanced/media/shadowtext01.png "ShadowText01")  
ソフト シャドウを適用したテキストの例  
  
 <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> プロパティを設定して、影の幅を制御できます。  値 `4.0` は、影の幅が 4 ピクセルであることを示します。  <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> プロパティを変更して、影のぼかしを制御できます。  値 `0.0` は、ぼかしがないことを示します。  ソフト シャドウを作成する方法を次のコード例に示します。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  シャドウ効果は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] テキスト レンダリング パイプラインを経由しません。  そのため、シャドウ効果を使用する場合、ClearType は無効です。  
  
 テキストにハード ドロップ シャドウ効果が適用されている例を次に示します。  ここでは、影のぼかしは使用されません。  
  
 ![ぼかし &#61; 0 のテキスト シャドウ](../../../../docs/framework/wpf/advanced/media/shadowtext02.png "ShadowText02")  
ハード シャドウを適用したテキストの例  
  
 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> プロパティを `0.0` に設定することで、ぼかしはまったく使用されなくなり、ハード シャドウを作成できます。  <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> プロパティを変更して、影の方向を制御できます。  このプロパティの方向の値を `0` から `360` の間の角度に設定します。  <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> プロパティで設定する方向の値を次の図に示します。  
  
 ![シャドウの DropShadow 度の設定](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
DropShadow 方向の図  
  
 ハード シャドウを作成する方法を次のコード例に示します。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## ぼかし効果の使用  
 <xref:System.Windows.Media.Effects.BlurBitmapEffect> を使用すると、影のような効果を作成して、テキスト オブジェクトの後ろに適用できます。  テキストに適用されるぼかしビットマップ効果は、テキストのすべての方向へ均等に、ぼかしを適用します。  
  
 テキストにぼかし効果が適用されている例を次に示します。  
  
 ![BlurBitmapEffect を使用するテキスト シャドウ](../../../../docs/framework/wpf/advanced/media/shadowtext06.png "ShadowText06")  
ぼかし効果を適用したテキストの例  
  
 ぼかし効果を作成する方法を次のコード例に示します。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## TranslateTransform の使用  
 <xref:System.Windows.Media.TranslateTransform> を使用すると、影のような効果を作成して、テキスト オブジェクトの後ろに適用できます。  
  
 <xref:System.Windows.Media.TranslateTransform> を使用してテキストをオフセットするコード例を次に示します。  この例では、主要なテキストの下のわずかにオフセットされたテキストのコピーにより、シャドウ効果が作成されます。  
  
 ![TranslateTransform を使用するテキスト シャドウ](../../../../docs/framework/wpf/advanced/media/shadowtext07.png "ShadowText07")  
シャドウ効果への変換を使用しているテキストの例  
  
 シャドウ効果への変換を作成する方法を次のコード例に示します。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]