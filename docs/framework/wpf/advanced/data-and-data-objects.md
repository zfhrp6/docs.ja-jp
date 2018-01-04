---
title: "データとデータ オブジェクト"
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
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb2354b61a0433981675ba55978f31937212cabc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="data-and-data-objects"></a><span data-ttu-id="55f9f-102">データとデータ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="55f9f-102">Data and Data Objects</span></span>
<span data-ttu-id="55f9f-103">ドラッグ アンド ドロップ操作の一部として転送されるデータは、データ オブジェクトに格納されます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-103">Data that is transferred as part of a drag-and-drop operation is stored in a data object.</span></span>  <span data-ttu-id="55f9f-104">概念的には、データ オブジェクトは、1 つ以上の次のペアで構成されます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-104">Conceptually, a data object consists of one or more of the following pairs:</span></span>  
  
-   <span data-ttu-id="55f9f-105"><xref:System.Object>実際のデータを格納しています。</span><span class="sxs-lookup"><span data-stu-id="55f9f-105">An <xref:System.Object> that contains the actual data.</span></span>  
  
-   <span data-ttu-id="55f9f-106">対応するデータ形式の識別子。</span><span class="sxs-lookup"><span data-stu-id="55f9f-106">A corresponding data format identifier.</span></span>  
  
 <span data-ttu-id="55f9f-107">データ自体をベースとして表すことができるもので構成できます<xref:System.Object>です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-107">The data itself can consist of anything that can be represented as a base <xref:System.Object>.</span></span>  <span data-ttu-id="55f9f-108">対応するデータ形式は、文字列または<xref:System.Type>では、データの書式設定についてのヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-108">The corresponding data format is a string or <xref:System.Type> that provides a hint about what format the data is in.</span></span>  <span data-ttu-id="55f9f-109">複数のデータ/データ形式のペア; をホストしているデータ オブジェクトのサポートこれにより、複数の形式でデータを提供する 1 つのデータ オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="55f9f-109">Data objects support hosting multiple data/data format pairs; this enables a single data object to provide data in multiple formats.</span></span>  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a><span data-ttu-id="55f9f-110">データ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="55f9f-110">Data Objects</span></span>  
 <span data-ttu-id="55f9f-111">すべてのデータ オブジェクトを実装する必要があります、<xref:System.Windows.IDataObject>次の標準セットを有効にして、データ転送を容易にするメソッドを提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="55f9f-111">All data objects must implement the <xref:System.Windows.IDataObject> interface, which provides the following standard set of methods that enable and facilitate data transfer.</span></span>  
  
|<span data-ttu-id="55f9f-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="55f9f-112">Method</span></span>|<span data-ttu-id="55f9f-113">まとめ</span><span class="sxs-lookup"><span data-stu-id="55f9f-113">Summary</span></span>|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|<span data-ttu-id="55f9f-114">指定したデータ形式のデータ オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-114">Retrieves a data object in a specified data format.</span></span>|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|<span data-ttu-id="55f9f-115">データで使用可能でまたは指定された形式に変換できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-115">Checks to see whether the data is available in, or can be converted to, a specified format.</span></span>|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|<span data-ttu-id="55f9f-116">このデータ オブジェクトのデータでは、またはに変換できる形式の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-116">Returns a list of formats that the data in this data object is stored in, or can be converted to.</span></span>|  
|<xref:System.Windows.IDataObject.SetData%2A>|<span data-ttu-id="55f9f-117">このデータ オブジェクトに指定されたデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-117">Stores the specified data in this data object.</span></span>|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="55f9f-118">基本実装を提供<xref:System.Windows.IDataObject>で、<xref:System.Windows.DataObject>クラスです。</span><span class="sxs-lookup"><span data-stu-id="55f9f-118"> provides a basic implementation of <xref:System.Windows.IDataObject> in the <xref:System.Windows.DataObject> class.</span></span> <span data-ttu-id="55f9f-119">ストック<xref:System.Windows.DataObject>クラスは多くの一般的なデータ転送のシナリオのための十分なです。</span><span class="sxs-lookup"><span data-stu-id="55f9f-119">The stock <xref:System.Windows.DataObject> class is sufficient for many common data transfer scenarios.</span></span>  
  
 <span data-ttu-id="55f9f-120">ビットマップ、CSV、ファイル、HTML、RTF、文字列、テキスト、およびオーディオなど、いくつかの定義済みの形式があります。</span><span class="sxs-lookup"><span data-stu-id="55f9f-120">There are several pre-defined formats, such as bitmap, CSV, file, HTML, RTF, string, text, and audio.</span></span> <span data-ttu-id="55f9f-121">提供される定義済みのデータ形式については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください、<xref:System.Windows.DataFormats>クラスのリファレンス トピックです。</span><span class="sxs-lookup"><span data-stu-id="55f9f-121">For information about pre-defined data formats provided with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see the <xref:System.Windows.DataFormats> class reference topic.</span></span>  
  
 <span data-ttu-id="55f9f-122">通常、データ オブジェクトでは、データの抽出中に 1 つの形式を別の形式で格納されているデータを自動的に変換するための機能この機能は、"自動変換"と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-122">Data objects commonly include a facility for automatically converting data stored in one format to a different format while extracting data; this facility is referred to as auto-convert.</span></span> <span data-ttu-id="55f9f-123">データ形式のデータ オブジェクトで使用可能な場合、クエリを実行するときに自動変換可能なデータ形式をフィルター処理するネイティブ データ形式から呼び出し、<xref:System.Windows.DataObject.GetFormats%28System.Boolean%29>または<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>メソッドを指定して、`autoConvert`パラメーターとして`false`です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-123">When querying for the data formats available in a data object, auto-convertible data formats can be filtered from native data formats by calling the <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> or <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> method and specifying the `autoConvert` parameter as `false`.</span></span>  <span data-ttu-id="55f9f-124">データを使用して、データ オブジェクトに追加するときに、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>を設定して、メソッドのデータの自動変換を禁止することができます、`autoConvert`パラメーターを`false`です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-124">When adding data to a data object with the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> method, auto-conversion of data can be prohibited by setting the `autoConvert` parameter to `false`.</span></span>  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a><span data-ttu-id="55f9f-125">データ オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="55f9f-125">Working with Data Objects</span></span>  
 <span data-ttu-id="55f9f-126">このセクションでは、データ オブジェクトの作成と操作の一般的な手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-126">This section describes common techniques for creating and working with data objects.</span></span>  
  
### <a name="creating-new-data-objects"></a><span data-ttu-id="55f9f-127">新しいデータ オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="55f9f-127">Creating New Data Objects</span></span>  
 <span data-ttu-id="55f9f-128"><xref:System.Windows.DataObject>クラスには、新しい設定を容易にするいくつかのオーバー ロードされたコンス トラクターが用意されています<xref:System.Windows.DataObject>1 つのデータ/データ形式のペアを持つインスタンス。</span><span class="sxs-lookup"><span data-stu-id="55f9f-128">The <xref:System.Windows.DataObject> class provides several overloaded constructors that facilitate populating a new <xref:System.Windows.DataObject> instance with a single data/data format pair.</span></span>  
  
 <span data-ttu-id="55f9f-129">次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して<xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) 文字列と指定したデータ形式でデータ オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-129">The following example code creates a new data object and uses one of the overloaded constructors <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="55f9f-130">データの形式が文字列で指定されたこのケースでは、<xref:System.Windows.DataFormats>クラスには、事前に定義された型の文字列のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="55f9f-130">In this case, the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="55f9f-131">既定では、格納されたデータの自動変換を許可します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-131">Auto-conversion of the stored data is allowed by default.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 <span data-ttu-id="55f9f-132">データ オブジェクトを作成するコードの例については、次を参照してください。[データ オブジェクトを作成](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md)です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-132">For more examples of code that creates a data object, see [Create a Data Object](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md).</span></span>  
  
### <a name="storing-data-in-multiple-formats"></a><span data-ttu-id="55f9f-133">複数の形式でデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-133">Storing Data in Multiple Formats</span></span>  
 <span data-ttu-id="55f9f-134">単一のデータ オブジェクトは、複数の形式でデータを格納することです。</span><span class="sxs-lookup"><span data-stu-id="55f9f-134">A single data object is able to store data in multiple formats.</span></span>   <span data-ttu-id="55f9f-135">1 つのデータ オブジェクト内の複数のデータ形式を戦略的に使用可能性のあるにより、データ オブジェクトのドロップ ターゲットをよりも多様なで使用できるだけの場合、1 つのデータ形式を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-135">Strategic use of multiple data formats within a single data object potentially makes the data object consumable by a wider variety of drop targets than if only a single data format could be represented.</span></span>  <span data-ttu-id="55f9f-136">なお、一般に、ドラッグ ソースがドロップ ターゲットを潜在的なデータ形式に依存しない必要があります。</span><span class="sxs-lookup"><span data-stu-id="55f9f-136">Note that, in general, a drag source must be agnostic about the data formats that are consumable by potential drop targets.</span></span>  
  
 <span data-ttu-id="55f9f-137">次の例を使用する方法を示しています、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>複数の形式でデータ オブジェクトにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-137">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a><span data-ttu-id="55f9f-138">使用可能な形式のデータ オブジェクトを照会します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-138">Querying a Data Object for Available Formats</span></span>  
 <span data-ttu-id="55f9f-139">単一のデータ オブジェクトには、データ形式の任意の数が含まれていることができます、ために、データ オブジェクトには、使用可能なデータ形式の一覧を取得するための機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-139">Because a single data object can contain an arbitrary number of data formats, data objects include facilities for retrieving a list of available data formats.</span></span>  
  
 <span data-ttu-id="55f9f-140">次のコード例を使用して、 <xref:System.Windows.DataObject.GetFormats%2A> (ネイティブおよび自動変換によって) データ オブジェクトで使用可能なすべてのデータ形式を示す文字列の配列を取得するオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="55f9f-140">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and by auto-convert).</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 <span data-ttu-id="55f9f-141">使用可能なデータ形式のデータ オブジェクトのクエリを実行するコードの例については、次を参照してください。[データ オブジェクト内のデータ形式を一覧表示](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md)です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-141">For more examples of code that queries a data object for available data formats, see [List the Data Formats in a Data Object](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md).</span></span>  <span data-ttu-id="55f9f-142">特定のデータ形式が存在するためのデータ オブジェクトを照会する例については、次を参照してください。[データ形式が存在かどうかを判断データ オブジェクトで](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md)です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-142">For examples of querying a data object for the presence of a particular data format, see [Determine if a Data Format is Present in a Data Object](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md).</span></span>  
  
### <a name="retrieving-data-from-a-data-object"></a><span data-ttu-id="55f9f-143">データ オブジェクトからのデータの取得</span><span class="sxs-lookup"><span data-stu-id="55f9f-143">Retrieving Data from a Data Object</span></span>  
 <span data-ttu-id="55f9f-144">いずれかの呼び出しでは、特定の形式でデータ オブジェクトからデータを取得するだけで、<xref:System.Windows.DataObject.GetData%2A>メソッドと目的のデータ形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-144">Retrieving data from a data object in a particular format simply involves calling one of the <xref:System.Windows.DataObject.GetData%2A> methods and specifying the desired data format.</span></span>  <span data-ttu-id="55f9f-145">1 つ、<xref:System.Windows.DataObject.GetDataPresent%2A>特定のデータ形式の存在をチェックするメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-145">One of the <xref:System.Windows.DataObject.GetDataPresent%2A> methods can be used to check for the presence of a particular data format.</span></span>  <span data-ttu-id="55f9f-146"><xref:System.Windows.DataObject.GetData%2A>内のデータを返します、<xref:System.Object>以外の場合は、データ形式によってこのオブジェクトは、型固有のコンテナーにキャストすることができます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-146"><xref:System.Windows.DataObject.GetData%2A> returns the data in an <xref:System.Object>; depending on the data format, this object can be cast to a type-specific container.</span></span>  
  
 <span data-ttu-id="55f9f-147">次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>のオーバー ロードを確認して、指定したデータ形式が使用可能なかどうか (ネイティブまたは自動変換)。</span><span class="sxs-lookup"><span data-stu-id="55f9f-147">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to check if a specified data format is available (native or by auto-convert).</span></span> <span data-ttu-id="55f9f-148">例を使用してデータを取得する場合は、指定した書式を使用できる、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="55f9f-148">If the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 <span data-ttu-id="55f9f-149">データ オブジェクトからデータを取得するコードの例については、次を参照してください。 [、特定のデータ形式でデータの取得](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md)です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-149">For more examples of code that retrieves data from a data object, see [Retrieve Data in a Particular Data Format](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md).</span></span>  
  
### <a name="removing-data-from-a-data-object"></a><span data-ttu-id="55f9f-150">データ オブジェクトからデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-150">Removing Data From a Data Object</span></span>  
 <span data-ttu-id="55f9f-151">データは、データ オブジェクトから直接削除できません。</span><span class="sxs-lookup"><span data-stu-id="55f9f-151">Data cannot be directly removed from a data object.</span></span>  <span data-ttu-id="55f9f-152">効果的にデータ オブジェクトからデータを削除するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-152">To effectively remove data from a data object, follow these steps:</span></span>  
  
1.  <span data-ttu-id="55f9f-153">保持するデータのみを格納する新しいデータ オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-153">Create a new data object that will contain only the data you want to retain.</span></span>  
  
2.  <span data-ttu-id="55f9f-154">""、必要なデータ old data オブジェクトから、新しいデータをオブジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="55f9f-154">"Copy" the desired data from the old data object to the new data object.</span></span>  <span data-ttu-id="55f9f-155">データをコピーするには、いずれかを使用、<xref:System.Windows.DataObject.GetData%2A>を取得するメソッド、<xref:System.Object>を生のデータを格納し、いずれかの<xref:System.Windows.DataObject.SetData%2A>新しいデータ オブジェクトにデータを追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="55f9f-155">To copy the data, use one of the <xref:System.Windows.DataObject.GetData%2A> methods to retrieve an <xref:System.Object> that contains the raw data, and then use one of the <xref:System.Windows.DataObject.SetData%2A> methods to add the data to the new data object.</span></span>  
  
3.  <span data-ttu-id="55f9f-156">古いデータ オブジェクトを新しいものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="55f9f-156">Replace the old data object with the new one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55f9f-157"><xref:System.Windows.DataObject.SetData%2A>メソッドは、データ オブジェクトをデータを追加するだけは、データとデータ形式が正確に前の呼び出しと同じ場合でも、データの置換は行いません。</span><span class="sxs-lookup"><span data-stu-id="55f9f-157">The <xref:System.Windows.DataObject.SetData%2A> methods only add data to a data object; they do not replace data, even if the data and data format are exactly the same as a previous call.</span></span> <span data-ttu-id="55f9f-158">呼び出す<xref:System.Windows.DataObject.SetData%2A>と同じデータに対して 2 回形式がデータ オブジェクトに 2 回含まれているデータ/データの形式で発生します。</span><span class="sxs-lookup"><span data-stu-id="55f9f-158">Calling <xref:System.Windows.DataObject.SetData%2A> twice for the same data and data format will result in the data/data format being present twice in the data object.</span></span>
