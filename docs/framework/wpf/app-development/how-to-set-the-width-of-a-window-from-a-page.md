---
title: '方法: ページから、ウィンドウの幅を設定'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: a0ae0e136e0b7f1cd2a2ec56455e14723e8fa306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545993"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>方法: ページから、ウィンドウの幅を設定
この例から、ウィンドウの幅を設定する方法を示しています、<xref:System.Windows.Controls.Page>です。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.Page>を設定して、そのホスト ウィンドウの幅を設定できます<xref:System.Windows.Controls.Page.WindowWidth%2A>です。 このプロパティにより、<xref:System.Windows.Controls.Page>をホストするウィンドウの種類の明示的な知識がないようにします。  
  
> [!NOTE]
>  使用してウィンドウの幅を設定する<xref:System.Windows.Controls.Page.WindowWidth%2A>、<xref:System.Windows.Controls.Page>ウィンドウの子でなければなりません。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
