---
title: "方法 : システム フォントを列挙する"
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
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ae03cbd8828f61011f8d806be32b5827d77b22a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enumerate-system-fonts"></a>方法 : システム フォントを列挙する
## <a name="example"></a>例  
 次の例では、システム フォントのコレクション内のフォントを列挙する方法を示します。 それぞれのフォント ファミリ名<xref:System.Windows.Media.FontFamily>内<xref:System.Windows.Media.Fonts.SystemFontFamilies%2A>コンボ ボックスにアイテムとして追加します。  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 同じフォント ファミリの複数のバージョンが、同じディレクトリに存在する場合、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]フォント列挙には、フォントの最新バージョンが返されます。 バージョン情報は、解決を提供していない、最新のタイムスタンプを持つフォントが返されます。 タイムスタンプ情報が同等の場合は、アルファベット順の最初のフォント ファイルが返されます。
