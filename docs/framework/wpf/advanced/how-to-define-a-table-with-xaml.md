---
title: "方法 : XAML を使用してテーブルを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 350dff0b6ea9d92e919e45e4f46cf888f44f6212
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a>方法 : XAML を使用してテーブルを定義する
次の例は、定義する方法を示します、<xref:System.Windows.Documents.Table>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  このテーブルには 4 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>要素) といくつかの行 (によって表される<xref:System.Windows.Documents.TableRow>要素) を含むデータもとしてタイトル、ヘッダーおよびフッター情報。  内の行を含める必要があります、<xref:System.Windows.Documents.TableRowGroup>要素。  テーブル内の各行は 1 つまたは複数のセルで構成されます (によって表される<xref:System.Windows.Documents.TableCell>要素)。  テーブル セル内のコンテンツに含まれる必要があります、<xref:System.Windows.Documents.Block>要素です。 ここでは<xref:System.Windows.Documents.Paragraph>要素が使用されます。  テーブルはハイパーリンクもホスト (によって表される、<xref:System.Windows.Documents.Hyperlink>要素) フッター行にします。  
  
## <a name="example"></a>例  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 この例で定義されたテーブルのレンダリング結果を次の図に示します。  
  
 ![描画されたテーブル。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")
