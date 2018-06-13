---
title: ISymUnmanagedVariable インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3db4fc691637c049e0374416cb92a2056555ad11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428701"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="0a0fa-102">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a0fa-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="0a0fa-103">パラメーター、ローカル変数またはフィールドなどの変数を表します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a0fa-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-104">Methods</span></span>  
  
|<span data-ttu-id="0a0fa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-105">Method</span></span>|<span data-ttu-id="0a0fa-106">説明</span><span class="sxs-lookup"><span data-stu-id="0a0fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a0fa-107">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="0a0fa-108">この変数の最初のアドレス フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="0a0fa-109">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="0a0fa-110">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="0a0fa-111">この変数の 2 番目のアドレス フィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="0a0fa-112">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="0a0fa-113">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="0a0fa-114">この変数のアドレスの 3 番目のフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="0a0fa-115">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="0a0fa-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="0a0fa-117">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="0a0fa-118">GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="0a0fa-119">この変数の属性のフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="0a0fa-120">GetEndOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="0a0fa-121">この変数内では、親の終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="0a0fa-122">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="0a0fa-123">この変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="0a0fa-124">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="0a0fa-125">この変数のシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="0a0fa-126">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0fa-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="0a0fa-127">この変数内では、親の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0fa-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a0fa-128">要件</span><span class="sxs-lookup"><span data-stu-id="0a0fa-128">Requirements</span></span>  
 <span data-ttu-id="0a0fa-129">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a0fa-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0fa-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a0fa-130">See Also</span></span>  
 [<span data-ttu-id="0a0fa-131">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a0fa-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
