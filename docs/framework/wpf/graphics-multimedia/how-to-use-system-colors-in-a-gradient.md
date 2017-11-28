---
title: "方法 : グラデーションでシステム カラーを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>方法 : グラデーションでシステム カラーを使用する
使用するシステムの色のグラデーションを使用するのには *\<SystemColor >*色と *\<SystemColor >*の静的なプロパティを (ゼロ)、<xref:System.Windows.SystemColors>クラスを取得する、色への参照場所 *\<SystemColor >*対象のシステム カラーの名前を指定します。 使用して、  *\<SystemColor >*(ゼロ) のプロパティをシステムのテーマの変更として自動的に更新される動的参照を作成するときにします。 それ以外の場合を使用して、  *\<SystemColor >*Color プロパティです。  
  
## <a name="example"></a>例  
 次の例では、動的なシステム カラー リソースを使用して、グラデーションを作成します。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 次の例では、静的なシステム カラー リソースを使用して、グラデーションを作成します。  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.SystemColors>  
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
