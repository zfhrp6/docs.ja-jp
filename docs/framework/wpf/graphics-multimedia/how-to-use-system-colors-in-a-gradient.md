---
title: "方法 : グラデーションでシステム カラーを使用する | Microsoft Docs"
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
  - "グラデーション, システム カラー"
  - "システム カラー (グラデーション)"
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : グラデーションでシステム カラーを使用する
グラデーションでシステム カラーを使用するには、<xref:System.Windows.SystemColors> クラスの静的プロパティ *\<SystemColor\>*Color と *\<SystemColor\>*ColorKey を使用して、色に対する参照を取得します。*\<SystemColor\>* は、目的のシステム カラーの名前です。  システム テーマが変更されると自動的に更新される動的な参照を作成するには、*\<SystemColor\>*ColorKey プロパティを使用します。  それ以外の場合は、*\<SystemColor\>*Color プロパティを使用します。  
  
## 使用例  
 次の例では、動的なシステム カラー リソースを使用してグラデーションを作成します。  
  
 [!code-xml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 次の例では、静的なシステム カラー リソースを使用してグラデーションを作成します。  
  
 [!code-xml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.SystemColors>   
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)