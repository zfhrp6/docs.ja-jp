---
title: "ISymUnmanagedMethod インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod
helpviewer_keywords: ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 030ea4b472f6a6aead307e0c5cc94dfb34c19992
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="e3762-102">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3762-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="e3762-103">シンボル ストア内のメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="e3762-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="e3762-104">このインターフェイスは、型に関連する属性ではなく、メソッドの symbol 関連の属性のみへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e3762-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3762-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-105">Methods</span></span>  
  
|<span data-ttu-id="e3762-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-106">Method</span></span>|<span data-ttu-id="e3762-107">説明</span><span class="sxs-lookup"><span data-stu-id="e3762-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3762-108">GetNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="e3762-109">このメソッドが定義されている外側の名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="e3762-110">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="e3762-111">ドキュメント内の指定位置に対応するこのメソッド内のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="e3762-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="e3762-112">GetParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="e3762-113">このメソッドのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="e3762-114">GetRanges メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="e3762-115">指定されたドキュメント内の位置には、Microsoft intermediate language (MSIL をこのメソッド内に含まれる位置) の範囲に先頭と末尾オフセットのペアの対応する配列を返します。</span><span class="sxs-lookup"><span data-stu-id="e3762-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="e3762-116">GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="e3762-117">このメソッド内でルート構文スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="e3762-118">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="e3762-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="e3762-119">GetScopeFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="e3762-120">このメソッドを指定したオフセットを囲む内で最も外側の構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="e3762-121">GetSequencePointCount メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="e3762-122">このメソッド内のシーケンス ポイントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="e3762-123">GetSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="e3762-124">このメソッド内のすべてのシーケンス ポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="e3762-125">GetSourceStartEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="e3762-126">このメソッドのソースの開始と終了のドキュメントの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="e3762-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="e3762-127">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="e3762-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="e3762-128">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="e3762-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3762-129">要件</span><span class="sxs-lookup"><span data-stu-id="e3762-129">Requirements</span></span>  
 <span data-ttu-id="e3762-130">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e3762-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3762-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3762-131">See Also</span></span>  
 [<span data-ttu-id="e3762-132">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="e3762-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
