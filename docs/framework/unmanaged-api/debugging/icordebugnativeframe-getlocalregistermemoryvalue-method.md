---
title: "ICorDebugNativeFrame::GetLocalRegisterMemoryValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58d48b8d3b45afe4018d80ce30066708085c517a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="15f0e-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="15f0e-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="15f0e-103">引数またはローカル変数、うち、下位ワードと上位ワードはメモリの場所に保存およびに指定された登録、それぞれ、このネイティブ フレームの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="15f0e-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f0e-104">構文</span><span class="sxs-lookup"><span data-stu-id="15f0e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15f0e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="15f0e-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="15f0e-106">[in]値の上位ワードを含むレジスタを指定する"CorDebugRegister"列挙の値です。</span><span class="sxs-lookup"><span data-stu-id="15f0e-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="15f0e-107">[in]A`CORDB_ADDRESS`値の下位ワードを含むメモリの場所を指定する値。</span><span class="sxs-lookup"><span data-stu-id="15f0e-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="15f0e-108">[in]によって参照されているバイナリ メタデータ シグネチャのサイズを指定する整数、`pvSigBlob`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="15f0e-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="15f0e-109">[in]A`PCCOR_SIGNATURE`値の型のバイナリ メタデータ シグネチャを指している値。</span><span class="sxs-lookup"><span data-stu-id="15f0e-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="15f0e-110">[out]指定した登録とメモリの場所に格納されている取得した値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="15f0e-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f0e-111">要件</span><span class="sxs-lookup"><span data-stu-id="15f0e-111">Requirements</span></span>  
 <span data-ttu-id="15f0e-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="15f0e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f0e-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15f0e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15f0e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15f0e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15f0e-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15f0e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f0e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="15f0e-116">See Also</span></span>  
 
