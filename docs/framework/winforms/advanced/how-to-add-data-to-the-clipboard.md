---
title: "方法 : クリップボードにデータを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 452dfc5a9645e8f43ab583099deec60faa2d1b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="72663-102">方法 : クリップボードにデータを追加する</span><span class="sxs-lookup"><span data-stu-id="72663-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="72663-103"><xref:System.Windows.Forms.Clipboard>クラスは、Windows オペレーティング システムのクリップボード機能との対話に使用できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="72663-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="72663-104">多くのアプリケーションでは、データの一時的なレポジトリとしてクリップボードを使用します。</span><span class="sxs-lookup"><span data-stu-id="72663-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="72663-105">たとえば、ワード プロセッサでは、カット アンド ペースト操作中に、クリップボードを使用します。</span><span class="sxs-lookup"><span data-stu-id="72663-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="72663-106">クリップボードも別の 1 つのアプリケーションからデータを転送するため便利です。</span><span class="sxs-lookup"><span data-stu-id="72663-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="72663-107">クリップボードにデータを追加するときは、他のアプリケーションは、その形式を使用する場合、データが認識できるように、データ形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="72663-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="72663-108">データを使用できるその他のアプリケーションの数を増やすには複数の異なる形式でクリップボードにデータを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="72663-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="72663-109">クリップボードの形式は、その形式を使用するアプリケーションが関連付けられているデータを取得できるようにする形式を識別する文字列です。</span><span class="sxs-lookup"><span data-stu-id="72663-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="72663-110"><xref:System.Windows.Forms.DataFormats>クラスは、使用できる定義済みの形式名を提供します。</span><span class="sxs-lookup"><span data-stu-id="72663-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="72663-111">独自の形式名を使用してもまたはオブジェクトの型の形式として使用できます。</span><span class="sxs-lookup"><span data-stu-id="72663-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="72663-112">1 つまたは複数の形式でクリップボードにデータを追加するには、使用、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="72663-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="72663-113">このメソッドを任意のオブジェクトを渡すことができますが、複数の形式でデータを追加する必要があります最初に、データを追加する別のオブジェクトが複数の形式を使用するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="72663-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="72663-114">データを追加する通常、<xref:System.Windows.Forms.DataObject>を実装する任意の型を使用することができますが、<xref:System.Windows.Forms.IDataObject>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="72663-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="72663-115">[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]クリップボードの基本的な作業を容易に設計された新しいメソッドを使用して、クリップボードに直接データを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="72663-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="72663-116">テキストなどの 1 つの一般的な形式でデータを操作する場合は、これらのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="72663-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72663-117">すべての Windows ベースのアプリケーションでは、クリップボードを共有します。</span><span class="sxs-lookup"><span data-stu-id="72663-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="72663-118">そのため、別のアプリケーションに切り替えると、内容は変更されることがします。</span><span class="sxs-lookup"><span data-stu-id="72663-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="72663-119"><xref:System.Windows.Forms.Clipboard>クラスは、シングル スレッド アパートメント (STA) モードに設定のスレッドでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="72663-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="72663-120">このクラスを使用することを確認、`Main`メソッドが付いて、<xref:System.STAThreadAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="72663-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="72663-121">オブジェクトをクリップボードに保存するのには、シリアル化可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="72663-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="72663-122">型をシリアル化可能にするを使用してマークする、<xref:System.SerializableAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="72663-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="72663-123">クリップボードのメソッドにシリアル化できないオブジェクトを渡すと、例外をスローせず、メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="72663-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="72663-124">シリアル化の詳細については、「<xref:System.Runtime.Serialization>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72663-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="72663-125">1 つの一般的な形式でクリップボードにデータを追加するには</span><span class="sxs-lookup"><span data-stu-id="72663-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="72663-126">使用して、 <xref:System.Windows.Forms.Clipboard.SetAudio%2A>、 <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、 <xref:System.Windows.Forms.Clipboard.SetImage%2A>、または<xref:System.Windows.Forms.Clipboard.SetText%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="72663-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="72663-127">これらのメソッドはでのみ使用可能な[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="72663-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="72663-128">カスタム形式でクリップボードにデータを追加するには</span><span class="sxs-lookup"><span data-stu-id="72663-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="72663-129">使用して、<xref:System.Windows.Forms.Clipboard.SetData%2A>カスタム形式の名前を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="72663-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="72663-130">このメソッドでのみ使用可能な[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="72663-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="72663-131">定義済みの形式名を使用することも、<xref:System.Windows.Forms.Clipboard.SetData%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="72663-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="72663-132">詳細については、「<xref:System.Windows.Forms.DataFormats>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72663-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="72663-133">複数の形式でクリップボードにデータを追加するには</span><span class="sxs-lookup"><span data-stu-id="72663-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="72663-134">使用して、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>メソッドを渡します、<xref:System.Windows.Forms.DataObject>データを格納します。</span><span class="sxs-lookup"><span data-stu-id="72663-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="72663-135">このメソッドを使用してデータのバージョンでクリップボードを追加する必要がありますよりも前[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="72663-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="72663-136">参照</span><span class="sxs-lookup"><span data-stu-id="72663-136">See Also</span></span>  
 [<span data-ttu-id="72663-137">ドラッグ アンド ドロップ操作とクリップボードのサポート</span><span class="sxs-lookup"><span data-stu-id="72663-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="72663-138">方法: クリップボードからデータを取得する</span><span class="sxs-lookup"><span data-stu-id="72663-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
