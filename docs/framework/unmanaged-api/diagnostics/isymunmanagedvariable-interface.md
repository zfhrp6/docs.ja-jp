---
title: "ISymUnmanagedVariable インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable
helpviewer_keywords: ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c32d5b66c575a21b4d390cff560b71f93aa31927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="49b2c-102">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49b2c-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="49b2c-103">パラメーター、ローカル変数またはフィールドなどの変数を表します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49b2c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-104">Methods</span></span>  
  
|<span data-ttu-id="49b2c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-105">Method</span></span>|<span data-ttu-id="49b2c-106">説明</span><span class="sxs-lookup"><span data-stu-id="49b2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49b2c-107">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="49b2c-108">この変数の最初のアドレス フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="49b2c-109">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="49b2c-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="49b2c-110">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="49b2c-111">この変数の 2 番目のアドレス フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="49b2c-112">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="49b2c-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="49b2c-113">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="49b2c-114">この変数のアドレスの 3 番目のフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="49b2c-115">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="49b2c-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="49b2c-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="49b2c-117">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="49b2c-118">GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="49b2c-119">この変数の属性のフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="49b2c-120">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="49b2c-121">この変数内では、親の終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="49b2c-122">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="49b2c-123">この変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="49b2c-124">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="49b2c-125">この変数のシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="49b2c-126">GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="49b2c-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="49b2c-127">この変数内では、親の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="49b2c-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49b2c-128">要件</span><span class="sxs-lookup"><span data-stu-id="49b2c-128">Requirements</span></span>  
 <span data-ttu-id="49b2c-129">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="49b2c-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b2c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="49b2c-130">See Also</span></span>  
 [<span data-ttu-id="49b2c-131">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="49b2c-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
