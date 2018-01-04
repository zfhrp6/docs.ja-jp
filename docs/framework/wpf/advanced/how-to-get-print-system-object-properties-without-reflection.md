---
title: "方法 : リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する"
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
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d93919f691b51d5f177b074e5d9cef2c140458e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="93d56-102">方法 : リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する</span><span class="sxs-lookup"><span data-stu-id="93d56-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="93d56-103">リフレクションを使用してオブジェクトのプロパティ (およびそれらのプロパティの型) と、アプリケーションのパフォーマンスが低下することができます。</span><span class="sxs-lookup"><span data-stu-id="93d56-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="93d56-104"><xref:System.Printing.IndexedProperties>名前空間は、リフレクションを使用してこの情報を取得するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="93d56-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93d56-105">例</span><span class="sxs-lookup"><span data-stu-id="93d56-105">Example</span></span>  
 <span data-ttu-id="93d56-106">これを行うための手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="93d56-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="93d56-107">型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="93d56-107">Create an instance of the type.</span></span> <span data-ttu-id="93d56-108">次の例では、型は、<xref:System.Printing.PrintQueue>に付属している型[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]、ほぼ同一であるコードがから派生した型を使用する必要が<xref:System.Printing.PrintSystemObject>です。</span><span class="sxs-lookup"><span data-stu-id="93d56-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="93d56-109">作成、<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>型から<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>です。</span><span class="sxs-lookup"><span data-stu-id="93d56-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="93d56-110"><xref:System.Collections.DictionaryEntry.Value%2A>このディクショナリ内の各エントリのプロパティから派生した型の 1 つのオブジェクトである<xref:System.Printing.IndexedProperties.PrintProperty>です。</span><span class="sxs-lookup"><span data-stu-id="93d56-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="93d56-111">ディクショナリのメンバーを列挙します。</span><span class="sxs-lookup"><span data-stu-id="93d56-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="93d56-112">各メンバーに、次のように操作します。</span><span class="sxs-lookup"><span data-stu-id="93d56-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="93d56-113">アップ キャストするには、各エントリの値<xref:System.Printing.IndexedProperties.PrintProperty>を使用して作成し、<xref:System.Printing.IndexedProperties.PrintProperty>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="93d56-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="93d56-114">型を取得、<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>のそれぞれの<xref:System.Printing.IndexedProperties.PrintProperty>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="93d56-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="93d56-115">参照</span><span class="sxs-lookup"><span data-stu-id="93d56-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="93d56-116">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="93d56-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="93d56-117">印刷の概要</span><span class="sxs-lookup"><span data-stu-id="93d56-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
