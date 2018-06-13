---
title: ICorDebugAppDomain2::GetArrayOrPointerType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3f0ca6d930b22f30fe9bbc5b5a04bf1e034f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405826"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="be206-102">ICorDebugAppDomain2::GetArrayOrPointerType メソッド</span><span class="sxs-lookup"><span data-stu-id="be206-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="be206-103">指定された型、ポインター、または指定した型への参照の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="be206-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be206-104">構文</span><span class="sxs-lookup"><span data-stu-id="be206-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be206-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be206-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="be206-106">[in]CorElementType 列挙型 (配列、ポインター、または参照) を作成する基になるネイティブ型を指定の値です。</span><span class="sxs-lookup"><span data-stu-id="be206-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="be206-107">[in]配列のランク (つまり、ディメンションの数)。</span><span class="sxs-lookup"><span data-stu-id="be206-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="be206-108">場合、この値は 0 をする必要があります`elementType`ポインターまたは参照型を指定します。</span><span class="sxs-lookup"><span data-stu-id="be206-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="be206-109">[in]配列の型を表す ICorDebugType オブジェクトへのポインター、ポインター、または参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="be206-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="be206-110">[out]アドレスへのポインター、`ICorDebugType`構築された配列、ポインター型、または参照を表すオブジェクトを入力します。</span><span class="sxs-lookup"><span data-stu-id="be206-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be206-111">コメント</span><span class="sxs-lookup"><span data-stu-id="be206-111">Remarks</span></span>  
 <span data-ttu-id="be206-112">値*elementType*次のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be206-112">The value of *elementType* must be one of the following:</span></span>  
  
-   <span data-ttu-id="be206-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="be206-113">ELEMENT_TYPE_PTR</span></span>  
  
-   <span data-ttu-id="be206-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="be206-114">ELEMENT_TYPE_BYREF</span></span>  
  
-   <span data-ttu-id="be206-115">ELEMENT_TYPE_ARRAY またはインポートする場合</span><span class="sxs-lookup"><span data-stu-id="be206-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="be206-116">場合の値*elementType* ELEMENT_TYPE_PTR または ELEMENT_TYPE_BYREF、 *nRank* 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="be206-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be206-117">要件</span><span class="sxs-lookup"><span data-stu-id="be206-117">Requirements</span></span>  
 <span data-ttu-id="be206-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="be206-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be206-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be206-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be206-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be206-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be206-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be206-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
