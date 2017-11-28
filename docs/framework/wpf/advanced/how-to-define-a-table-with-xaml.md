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
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="fafe8-102">方法 : XAML を使用してテーブルを定義する</span><span class="sxs-lookup"><span data-stu-id="fafe8-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="fafe8-103">次の例は、定義する方法を示します、<xref:System.Windows.Documents.Table>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="fafe8-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="fafe8-104">このテーブルには 4 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>要素) といくつかの行 (によって表される<xref:System.Windows.Documents.TableRow>要素) を含むデータもとしてタイトル、ヘッダーおよびフッター情報。</span><span class="sxs-lookup"><span data-stu-id="fafe8-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="fafe8-105">内の行を含める必要があります、<xref:System.Windows.Documents.TableRowGroup>要素。</span><span class="sxs-lookup"><span data-stu-id="fafe8-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="fafe8-106">テーブル内の各行は 1 つまたは複数のセルで構成されます (によって表される<xref:System.Windows.Documents.TableCell>要素)。</span><span class="sxs-lookup"><span data-stu-id="fafe8-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="fafe8-107">テーブル セル内のコンテンツに含まれる必要があります、<xref:System.Windows.Documents.Block>要素です。 ここでは<xref:System.Windows.Documents.Paragraph>要素が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fafe8-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="fafe8-108">テーブルはハイパーリンクもホスト (によって表される、<xref:System.Windows.Documents.Hyperlink>要素) フッター行にします。</span><span class="sxs-lookup"><span data-stu-id="fafe8-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fafe8-109">例</span><span class="sxs-lookup"><span data-stu-id="fafe8-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="fafe8-110">この例で定義されたテーブルのレンダリング結果を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="fafe8-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="fafe8-111">![描画されたテーブル。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="fafe8-111">![Rendered table.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span></span>
