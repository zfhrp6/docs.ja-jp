---
title: "方法 : システム フォントを列挙する | Microsoft Docs"
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
  - "列挙, システム フォント"
  - "フォント, 列挙"
  - "システム フォント, 列挙"
  - "タイポグラフィ, 列挙 (システム フォントを)"
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : システム フォントを列挙する
## 使用例  
 次の例では、システム フォント コレクション内のフォントを列挙する方法を示しています。  <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> 内の各 <xref:System.Windows.Media.FontFamily> のフォント ファミリ名は、コンボ ボックスに項目として追加されます。  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 同じフォント ファミリの複数のバージョンが同じディレクトリに存在する場合、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のフォント列挙体は、そのフォントの最新のバージョンを返します。  バージョン情報で解決できない場合は、タイムスタンプが最新のフォントが返されます。  タイムスタンプ情報が同じである場合は、アルファベット順で最初のフォント ファイルが返されます。