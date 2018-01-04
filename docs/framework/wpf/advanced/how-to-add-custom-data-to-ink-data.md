---
title: "方法 : インク データにカスタム データを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ca44d6a2c42219f7aec76f8007010c24c610138
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="7a2c7-102">方法 : インク データにカスタム データを追加する</span><span class="sxs-lookup"><span data-stu-id="7a2c7-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="7a2c7-103">カスタム データは、インクがシリアル化するインク形式 (ISF) として保存されるときに保存されるインクを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="7a2c7-104">カスタム データを保存することができます、 <xref:System.Windows.Ink.DrawingAttributes>、 <xref:System.Windows.Ink.StrokeCollection>、または<xref:System.Windows.Ink.Stroke>です。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="7a2c7-105">3 つのオブジェクトのカスタム データを保存できることと、データを保存する最適な場所を決定する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="7a2c7-106">3 つすべてのクラスでは、同様のメソッドを使用して格納し、カスタム データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="7a2c7-107">カスタム データとしては、次の種類のみを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-107">Only the following types can be saved as custom data:</span></span>  
  
-   <xref:System.Boolean>  
  
-   <span data-ttu-id="7a2c7-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-108"><xref:System.Boolean>[]</span></span>  
  
-   <xref:System.Byte>  
  
-   <span data-ttu-id="7a2c7-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-109"><xref:System.Byte>[]</span></span>  
  
-   <xref:System.Char>  
  
-   <span data-ttu-id="7a2c7-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-110"><xref:System.Char>[]</span></span>  
  
-   <xref:System.DateTime>  
  
-   <span data-ttu-id="7a2c7-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-111"><xref:System.DateTime>[]</span></span>  
  
-   <xref:System.Decimal>  
  
-   <span data-ttu-id="7a2c7-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-112"><xref:System.Decimal>[]</span></span>  
  
-   <xref:System.Double>  
  
-   <span data-ttu-id="7a2c7-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-113"><xref:System.Double>[]</span></span>  
  
-   <xref:System.Int16>  
  
-   <span data-ttu-id="7a2c7-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-114"><xref:System.Int16>[]</span></span>  
  
-   <xref:System.Int32>  
  
-   <span data-ttu-id="7a2c7-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-115"><xref:System.Int32>[]</span></span>  
  
-   <xref:System.Int64>  
  
-   <span data-ttu-id="7a2c7-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-116"><xref:System.Int64>[]</span></span>  
  
-   <xref:System.Single>  
  
-   <span data-ttu-id="7a2c7-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-117"><xref:System.Single>[]</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <span data-ttu-id="7a2c7-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-118"><xref:System.UInt16>[]</span></span>  
  
-   <xref:System.UInt32>  
  
-   <span data-ttu-id="7a2c7-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-119"><xref:System.UInt32>[]</span></span>  
  
-   <xref:System.UInt64>  
  
-   <span data-ttu-id="7a2c7-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="7a2c7-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a2c7-121">例</span><span class="sxs-lookup"><span data-stu-id="7a2c7-121">Example</span></span>  
 <span data-ttu-id="7a2c7-122">次の例では、追加のカスタム データを取得する方法、<xref:System.Windows.Ink.StrokeCollection>です。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="7a2c7-123">次の例を表示するアプリケーションの作成、<xref:System.Windows.Controls.InkCanvas>と 2 つのボタンです。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="7a2c7-124">ボタン、 `switchAuthor`、2 つの異なる作成者によって使用される 2 つのペンを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="7a2c7-125">ボタン`changePenColors`上線の色を変更、<xref:System.Windows.Controls.InkCanvas>作成者に従ってします。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="7a2c7-126">2 つのアプリケーション定義<xref:System.Windows.Ink.DrawingAttributes>オブジェクトし、を描いていましたが、著者を示す 1 つずつにカスタム プロパティを追加、<xref:System.Windows.Ink.Stroke>です。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="7a2c7-127">ユーザーがクリックしたとき`changePenColors`アプリケーションがカスタム プロパティの値に従って stroke の外観を変更します。</span><span class="sxs-lookup"><span data-stu-id="7a2c7-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
