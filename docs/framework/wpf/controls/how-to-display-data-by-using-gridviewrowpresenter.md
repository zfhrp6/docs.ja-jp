---
title: "方法 : GridViewRowPresenter を使用してデータを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebe0a47d38a2cfda2a7d150b4a3886d9f63ee190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a><span data-ttu-id="315c7-102">方法 : GridViewRowPresenter を使用してデータを表示する</span><span class="sxs-lookup"><span data-stu-id="315c7-102">How to: Display Data by Using GridViewRowPresenter</span></span>
<span data-ttu-id="315c7-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.GridViewRowPresenter>と<xref:System.Windows.Controls.GridViewHeaderRowPresenter>列にデータを表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="315c7-103">This example shows how to use the <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects to display data in columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="315c7-104">例</span><span class="sxs-lookup"><span data-stu-id="315c7-104">Example</span></span>  
 <span data-ttu-id="315c7-105">次の例を指定する方法を示しています、<xref:System.Windows.Controls.GridViewColumnCollection>を表示する、<xref:System.DateTime.DayOfWeek%2A>と<xref:System.DateTime.Year%2A>の<xref:System.DateTime>オブジェクトを使用して<xref:System.Windows.Controls.GridViewRowPresenter>と<xref:System.Windows.Controls.GridViewHeaderRowPresenter>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="315c7-105">The following example shows how to specify a <xref:System.Windows.Controls.GridViewColumnCollection> that displays the <xref:System.DateTime.DayOfWeek%2A> and <xref:System.DateTime.Year%2A> of a <xref:System.DateTime> object by using <xref:System.Windows.Controls.GridViewRowPresenter> and <xref:System.Windows.Controls.GridViewHeaderRowPresenter> objects.</span></span> <span data-ttu-id="315c7-106">また、<xref:System.Windows.Style>の<xref:System.Windows.Controls.GridViewColumn.Header%2A>の<xref:System.Windows.Controls.GridViewColumn>です。</span><span class="sxs-lookup"><span data-stu-id="315c7-106">The example also defines a <xref:System.Windows.Style> for the <xref:System.Windows.Controls.GridViewColumn.Header%2A> of a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a><span data-ttu-id="315c7-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="315c7-107">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [<span data-ttu-id="315c7-108">GridView の概要</span><span class="sxs-lookup"><span data-stu-id="315c7-108">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
