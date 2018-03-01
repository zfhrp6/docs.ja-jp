---
title: "ICorDebugNativeFrame::GetLocalDoubleRegisterValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ece07fcffbc0d0e6b8cf06cc04866c1b651e6a01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="34afb-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="34afb-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="34afb-103">引数またはこのネイティブ フレームの指定した 2 つのレジスタに格納されているローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="34afb-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34afb-104">構文</span><span class="sxs-lookup"><span data-stu-id="34afb-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34afb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34afb-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="34afb-106">[in]値の上位ワードを含むレジスタを指定する"CorDebugRegister"列挙の値です。</span><span class="sxs-lookup"><span data-stu-id="34afb-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="34afb-107">[in]値、`CorDebugRegister`値の下位ワードを含むレジスタを指定する列挙体です。</span><span class="sxs-lookup"><span data-stu-id="34afb-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="34afb-108">[in]によって参照されているバイナリ メタデータ シグネチャのサイズを指定する整数、`pvSigBlob`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="34afb-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="34afb-109">[in]A`PCCOR_SIGNATURE`値の型のバイナリ メタデータ シグネチャを指している値。</span><span class="sxs-lookup"><span data-stu-id="34afb-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="34afb-110">[out]指定されたレジスタに格納されている取得した値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="34afb-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34afb-111">コメント</span><span class="sxs-lookup"><span data-stu-id="34afb-111">Remarks</span></span>  
 <span data-ttu-id="34afb-112">`GetLocalDoubleRegisterValue`ネイティブ フレームまたは、ジャスト イン-タイム (JIT) のいずれか、メソッドを使用できます-フレームをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="34afb-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34afb-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="34afb-113">Requirements</span></span>  
 <span data-ttu-id="34afb-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="34afb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34afb-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34afb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34afb-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34afb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34afb-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34afb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34afb-118">参照</span><span class="sxs-lookup"><span data-stu-id="34afb-118">See Also</span></span>  
 
