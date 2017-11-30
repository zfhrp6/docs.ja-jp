---
title: "方法: ページから、ウィンドウの高さを設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29de47eceae4b8927f2701ca0bbda2ecc7243919
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>方法: ページから、ウィンドウの高さを設定
この例から、ウィンドウの高さを設定する方法を示しています、<xref:System.Windows.Controls.Page>です。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.Page>を設定して、そのホスト ウィンドウの高さを設定できます<xref:System.Windows.Controls.Page.WindowHeight%2A>です。 このプロパティにより、<xref:System.Windows.Controls.Page>をホストするウィンドウの種類の明示的な知識がないようにします。  
  
> [!NOTE]
>  使用してウィンドウの高さを設定する<xref:System.Windows.Controls.Page.WindowHeight%2A>、<xref:System.Windows.Controls.Page>ウィンドウの子でなければなりません。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
