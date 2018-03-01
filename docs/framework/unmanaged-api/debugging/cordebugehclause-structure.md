---
title: "CorDebugEHClause 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 97428837d78c246915381b51fb5005a68518b7bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="2f715-102">CorDebugEHClause 構造体</span><span class="sxs-lookup"><span data-stu-id="2f715-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="2f715-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="2f715-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2f715-104">中間言語 (IL) コードの特定の部分の例外処理 (EH) 句を表しています。</span><span class="sxs-lookup"><span data-stu-id="2f715-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f715-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f715-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="2f715-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f715-106">Members</span></span>  
  
|<span data-ttu-id="2f715-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f715-107">Member</span></span>|<span data-ttu-id="2f715-108">説明</span><span class="sxs-lookup"><span data-stu-id="2f715-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="2f715-109">EH 句の例外情報について説明しているビット フィールド。</span><span class="sxs-lookup"><span data-stu-id="2f715-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="2f715-110">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f715-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="2f715-111">メソッド本体の先頭からの `try` ブロックのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2f715-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="2f715-112">`try` ブロックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2f715-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="2f715-113">この `try` ブロックのハンドラーの場所。</span><span class="sxs-lookup"><span data-stu-id="2f715-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="2f715-114">ハンドラー コードのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2f715-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="2f715-115">型に基づく例外ハンドラーのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="2f715-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="2f715-116">フィルターに基づく例外ハンドラーのメソッド本体の先頭からのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2f715-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f715-117">コメント</span><span class="sxs-lookup"><span data-stu-id="2f715-117">Remarks</span></span>  
 <span data-ttu-id="2f715-118">配列`CoreDebugEHClause`によって値が返される、 [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2f715-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="2f715-119">EH 句の情報は CLI 仕様によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="2f715-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="2f715-120">詳細については、次を参照してください。[標準の ECMA-355: 共通言語基盤 (CLI), 6 Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm)です。</span><span class="sxs-lookup"><span data-stu-id="2f715-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="2f715-121">`flags` フィールドには、次のフラグを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2f715-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="2f715-122">これらは、CorDebug.idl または CorDebug.h に定義されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2f715-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="2f715-123">フラグ</span><span class="sxs-lookup"><span data-stu-id="2f715-123">Flag</span></span>|<span data-ttu-id="2f715-124">値</span><span class="sxs-lookup"><span data-stu-id="2f715-124">Value</span></span>|<span data-ttu-id="2f715-125">説明</span><span class="sxs-lookup"><span data-stu-id="2f715-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="2f715-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="2f715-126">0x00000000</span></span>|<span data-ttu-id="2f715-127">入力された例外句。</span><span class="sxs-lookup"><span data-stu-id="2f715-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="2f715-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="2f715-128">0x00000001</span></span>|<span data-ttu-id="2f715-129">例外フィルターおよびハンドラー句。</span><span class="sxs-lookup"><span data-stu-id="2f715-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="2f715-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="2f715-130">0x00000002</span></span>|<span data-ttu-id="2f715-131">`finally` 句。</span><span class="sxs-lookup"><span data-stu-id="2f715-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="2f715-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="2f715-132">0x00000004</span></span>|<span data-ttu-id="2f715-133">fault 句 (例外がスローされた場合にのみ `finally` 句が呼び出される)。</span><span class="sxs-lookup"><span data-stu-id="2f715-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f715-134">必要条件</span><span class="sxs-lookup"><span data-stu-id="2f715-134">Requirements</span></span>  
 <span data-ttu-id="2f715-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f715-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f715-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f715-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f715-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f715-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f715-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f715-138">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f715-139">参照</span><span class="sxs-lookup"><span data-stu-id="2f715-139">See Also</span></span>  
 [<span data-ttu-id="2f715-140">GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="2f715-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [<span data-ttu-id="2f715-141">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="2f715-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
