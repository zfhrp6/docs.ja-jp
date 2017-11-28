---
title: "方法 : サムネイルとしてイメージを読み込む"
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
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: adcbd5fb82ce9ae89ac59db5aeb7f384f8cc1fc7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>方法 : サムネイルとしてイメージを読み込む
次の例を読み込む方法を示して、<xref:System.Windows.Controls.Image>アプリケーション メモリを節約するサムネイルとして。  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>のプロパティ、<xref:System.Windows.Media.Imaging.BitmapImage>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]イメージの読み込みに必要なメモリを減らします。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>のプロパティ、<xref:System.Windows.Media.Imaging.BitmapImage>イメージの読み込みに必要なメモリ量を減らすにはコードでします。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>関連項目  
 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
