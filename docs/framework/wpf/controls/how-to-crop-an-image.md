---
title: "方法 : イメージをトリミングする | Microsoft Docs"
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
  - "クラス, CroppedBitmap"
  - "CroppedBitmap クラス"
  - "トリミング (イメージを)"
  - "イメージ, トリミング"
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : イメージをトリミングする
この例では、<xref:System.Windows.Media.Imaging.CroppedBitmap> を使用してイメージをトリミングする方法を示します。  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> は、主にイメージのトリミングされたバージョンをエンコードしてファイルに保存する際に使用されます。  表示する目的でイメージをトリミングするには、「[Create a Clip Region](http://msdn.microsoft.com/ja-jp/56e4bed6-78d7-4292-b917-d72d0b3e4376)」を参照してください。  
  
## 使用例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] は、以下のサンプル内で使用するリソースを定義しています。  
  
 [!code-xml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> をイメージ ソースとして使用してイメージを作成する例を次に示します。  
  
 [!code-xml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> は、別の <xref:System.Windows.Media.Imaging.CroppedBitmap> のソースとして使用して、トリミングされたイメージをつなぎ合わせることもできます。  <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> は、最初のイメージではなく、ソースとなるトリミングされたビットマップを基準とした値を使用することに注意してください。  
  
 [!code-xml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## 参照  
 [Create a Clip Region](http://msdn.microsoft.com/ja-jp/56e4bed6-78d7-4292-b917-d72d0b3e4376)