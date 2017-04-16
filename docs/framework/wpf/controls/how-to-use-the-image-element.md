---
title: "方法 : イメージ要素を使用する | Microsoft Docs"
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
  - "BitmapImage クラス"
  - "クラス, BitmapImage"
  - "コントロール, イメージ"
  - "Image コントロール"
  - "描画 (イメージを)"
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : イメージ要素を使用する
この例では、<xref:System.Windows.Controls.Image> 要素を使用してアプリケーションにイメージを含める方法を示します。  
  
## 使用例  
 幅が 200 ピクセルのイメージをレンダリングする方法を次の例に示します。  この [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、属性構文とプロパティ タグ構文はどちらもイメージを定義するために使用されています。  属性およびプロパティの構文については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  <xref:System.Windows.Media.Imaging.BitmapImage> はイメージのソース データを定義するために使用されており、プロパティ タグ構文の例に対して明示的に定義されています。  また、<xref:System.Windows.Media.Imaging.BitmapImage> の <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> は、<xref:System.Windows.Controls.Image> の <xref:System.Windows.FrameworkElement.Width%2A> と同じ幅に設定されています。  これは、イメージのレンダリングに使用されるメモリの消費量を最小限に抑えるためです。  
  
> [!NOTE]
>  一般的に、レンダリングされたイメージのサイズを指定する場合は、<xref:System.Windows.FrameworkElement.Width%2A> または <xref:System.Windows.FrameworkElement.Height%2A> の一方のみを指定し、両方は指定しません。  いずれか一方を指定すると、イメージの[縦横比](GTMT)を保つことができます。  両方指定すると、予期しないイメージの拡大やゆがみが発生する場合があります。  イメージの拡大動作を制御するには、<xref:System.Windows.Controls.Image.Stretch%2A> プロパティおよび <xref:System.Windows.Controls.Image.StretchDirection%2A> プロパティを使用します。  
  
> [!NOTE]
>  イメージのサイズを <xref:System.Windows.FrameworkElement.Width%2A> または <xref:System.Windows.FrameworkElement.Height%2A> で指定した場合、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> または <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> も同じように対応させて設定する必要があります。  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> プロパティは、イメージ ソースを引き伸ばしてイメージ要素を埋める方法を示します。  詳細については、<xref:System.Windows.Media.Stretch> 列挙体の解説を参照してください。  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## 使用例  
 コードを使用して幅が 200 ピクセルのイメージをレンダリングする方法を次の例に示します。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> プロパティは、<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>\/<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> ブロック内で設定する必要があります。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## 参照  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)