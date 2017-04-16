---
title: "方法 : システム ブラシで領域を塗りつぶす | Microsoft Docs"
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
  - "ブラシ, 塗りつぶし (システム ブラシによる)"
  - "描画, システム ブラシで"
  - "システム ブラシ, 塗りつぶし"
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : システム ブラシで領域を塗りつぶす
<xref:System.Windows.SystemColors> クラスを使用すると、<xref:System.Windows.SystemColors.ControlBrush%2A>、<xref:System.Windows.SystemColors.ControlBrushKey%2A>、<xref:System.Windows.SystemColors.DesktopBrush%2A> などのシステム ブラシやシステム カラーにアクセスできます。  システム ブラシは、指定したシステム カラーで領域を塗りつぶす <xref:System.Windows.Media.SolidColorBrush> オブジェクトです。  システム ブラシは、常に純色の塗りつぶしを生成します。グラデーションを作成するためには使用できません。  
  
 システム ブラシは、静的なリソースとしても、動的なリソースとしても使用できます。  アプリケーションの実行中にユーザーがシステム ブラシを変更したときにブラシを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  SystemColors クラスには、厳密な名前付け規則に従うさまざまな静的プロパティが含まれます。  
  
-   *\<SystemColor\>*Brush  
  
     指定したシステム カラーの <xref:System.Windows.Media.SolidColorBrush> に対する静的参照を取得します。  
  
-   *\<SystemColor\>*BrushKey  
  
     指定したシステム カラーの <xref:System.Windows.Media.SolidColorBrush> に対する動的参照を取得します。  
  
-   *\<SystemColor\>*Color  
  
     指定したシステム カラーの <xref:System.Windows.Media.Color> 構造体に対する静的参照を取得します。  
  
-   *\<SystemColor\>*ColorKey  
  
     指定したシステム カラーの <xref:System.Windows.Media.Color> 構造体に対する動的参照を取得します。  
  
 システム カラーは <xref:System.Windows.Media.Color> 構造体であり、ブラシの構成に使用できます。  たとえば、<xref:System.Windows.Media.LinearGradientBrush> オブジェクトのグラデーション終了位置の <xref:System.Windows.Media.GradientStop.Color%2A> プロパティにシステム カラーを設定することで、システム カラーを使用してグラデーションを作成できます。  例については、「[グラデーションでシステム カラーを使用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)」を参照してください。  
  
## 使用例  
 次の例では、動的システム ブラシ参照を使用して、ボタンの背景を設定しています。  
  
 [!code-xml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 次の例では、静的システム ブラシ参照を使用して、ボタンの背景を設定しています。  
  
 [!code-xml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 グラデーションでのシステム カラーの使用方法を示す例については、「[グラデーションでシステム カラーを使用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)」を参照してください。  
  
## 参照  
 [グラデーションでシステム カラーを使用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)