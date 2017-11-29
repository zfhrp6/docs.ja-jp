---
title: "方法 : データ オブジェクトを作成する"
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
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7b002e1c7a9eea2592de58aac3b838b9f6f982ce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="27284-102">方法 : データ オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="27284-102">How to: Create a Data Object</span></span>
<span data-ttu-id="27284-103">次の例は、によって提供されるコンス トラクターを使用して、データ オブジェクトを作成するさまざまな方法を示して、<xref:System.Windows.DataObject>クラスです。</span><span class="sxs-lookup"><span data-stu-id="27284-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27284-104">例</span><span class="sxs-lookup"><span data-stu-id="27284-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27284-105">説明</span><span class="sxs-lookup"><span data-stu-id="27284-105">Description</span></span>  
 <span data-ttu-id="27284-106">次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) を文字列でデータ オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="27284-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="27284-107">ここでは、格納されたデータの種類に応じて、適切なデータ形式が自動的に決定し、既定では、格納されたデータの自動変換は許可されています。</span><span class="sxs-lookup"><span data-stu-id="27284-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-108">コード</span><span class="sxs-lookup"><span data-stu-id="27284-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="27284-109">説明</span><span class="sxs-lookup"><span data-stu-id="27284-109">Description</span></span>  
 <span data-ttu-id="27284-110">次のコード例は、上記のコードの圧縮バージョンです。</span><span class="sxs-lookup"><span data-stu-id="27284-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-111">コード</span><span class="sxs-lookup"><span data-stu-id="27284-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="27284-112">例</span><span class="sxs-lookup"><span data-stu-id="27284-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27284-113">説明</span><span class="sxs-lookup"><span data-stu-id="27284-113">Description</span></span>  
 <span data-ttu-id="27284-114">次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) 文字列と指定したデータ形式でデータ オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="27284-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="27284-115">ここでは、データ形式は文字列です。<xref:System.Windows.DataFormats>クラスには、事前に定義された型の文字列のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="27284-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="27284-116">既定では、格納されたデータの自動変換は許可されています。</span><span class="sxs-lookup"><span data-stu-id="27284-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-117">コード</span><span class="sxs-lookup"><span data-stu-id="27284-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="27284-118">説明</span><span class="sxs-lookup"><span data-stu-id="27284-118">Description</span></span>  
 <span data-ttu-id="27284-119">次のコード例は、上記のコードの圧縮バージョンです。</span><span class="sxs-lookup"><span data-stu-id="27284-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-120">コード</span><span class="sxs-lookup"><span data-stu-id="27284-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="27284-121">例</span><span class="sxs-lookup"><span data-stu-id="27284-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27284-122">説明</span><span class="sxs-lookup"><span data-stu-id="27284-122">Description</span></span>  
 <span data-ttu-id="27284-123">次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して (<xref:System.Windows.DataObject.%23ctor%2A>) 文字列と指定したデータ形式でデータ オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="27284-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="27284-124">ここでは、データ形式は、<xref:System.Type>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="27284-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="27284-125">既定では、格納されたデータの自動変換は許可されています。</span><span class="sxs-lookup"><span data-stu-id="27284-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-126">コード</span><span class="sxs-lookup"><span data-stu-id="27284-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="27284-127">説明</span><span class="sxs-lookup"><span data-stu-id="27284-127">Description</span></span>  
 <span data-ttu-id="27284-128">次のコード例は、上記のコードの圧縮バージョンです。</span><span class="sxs-lookup"><span data-stu-id="27284-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-129">コード</span><span class="sxs-lookup"><span data-stu-id="27284-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="27284-130">例</span><span class="sxs-lookup"><span data-stu-id="27284-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27284-131">説明</span><span class="sxs-lookup"><span data-stu-id="27284-131">Description</span></span>  
 <span data-ttu-id="27284-132">次のコード例は、新しいデータ オブジェクトを作成し、オーバー ロードされたコンス トラクターのいずれかを使用して (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) 文字列と指定したデータ形式でデータ オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="27284-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="27284-133">ここでは、データ形式は文字列です。<xref:System.Windows.DataFormats>クラスには、事前に定義された型の文字列のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="27284-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="27284-134">この特定のコンス トラクター オーバー ロードには、自動変換は許可されているかどうかを指定する、呼び出し元が有効です。</span><span class="sxs-lookup"><span data-stu-id="27284-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-135">コード</span><span class="sxs-lookup"><span data-stu-id="27284-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="27284-136">説明</span><span class="sxs-lookup"><span data-stu-id="27284-136">Description</span></span>  
 <span data-ttu-id="27284-137">次のコード例は、上記のコードの圧縮バージョンです。</span><span class="sxs-lookup"><span data-stu-id="27284-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="27284-138">コード</span><span class="sxs-lookup"><span data-stu-id="27284-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="27284-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="27284-139">See Also</span></span>  
 <xref:System.Windows.IDataObject>
