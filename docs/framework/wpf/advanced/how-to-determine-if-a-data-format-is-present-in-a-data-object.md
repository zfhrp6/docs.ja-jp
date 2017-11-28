---
title: "方法 : データ形式がデータ オブジェクトに存在するかどうかを判別する"
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
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e5eaad64e18ff955340a8e91bfe8bd0e09dd8d7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="51422-102">方法 : データ形式がデータ オブジェクトに存在するかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="51422-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="51422-103">次の例は、さまざまな使用方法を示して<xref:System.Windows.DataObject.GetDataPresent%2A>特定のデータ形式は、データ オブジェクトに存在するかどうかをクエリ メソッドはオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="51422-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51422-104">例</span><span class="sxs-lookup"><span data-stu-id="51422-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="51422-105">説明</span><span class="sxs-lookup"><span data-stu-id="51422-105">Description</span></span>  
 <span data-ttu-id="51422-106">次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>記述子の文字列によって特定のデータ形式の存在をクエリするオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="51422-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="51422-107">コード</span><span class="sxs-lookup"><span data-stu-id="51422-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="51422-108">例</span><span class="sxs-lookup"><span data-stu-id="51422-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="51422-109">説明</span><span class="sxs-lookup"><span data-stu-id="51422-109">Description</span></span>  
 <span data-ttu-id="51422-110">次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.Type%29>型によって特定のデータ形式の存在をクエリするオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="51422-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="51422-111">コード</span><span class="sxs-lookup"><span data-stu-id="51422-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="51422-112">例</span><span class="sxs-lookup"><span data-stu-id="51422-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="51422-113">説明</span><span class="sxs-lookup"><span data-stu-id="51422-113">Description</span></span>  
 <span data-ttu-id="51422-114">次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>記述子文字列でデータを照会するオーバー ロードし、自動変換可能なデータ形式を処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="51422-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="51422-115">コード</span><span class="sxs-lookup"><span data-stu-id="51422-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="51422-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="51422-116">See Also</span></span>  
 <xref:System.Windows.IDataObject>
