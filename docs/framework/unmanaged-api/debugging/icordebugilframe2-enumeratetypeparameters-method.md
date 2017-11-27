---
title: "ICorDebugILFrame2::EnumerateTypeParameters メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebc2496d633c04c94e94be201956daab38b79224
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="bd851-102">ICorDebugILFrame2::EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="bd851-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="bd851-103">含む ICorDebugTypeEnum オブジェクトを取得、<xref:System.Type>このフレーム内のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="bd851-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd851-104">構文</span><span class="sxs-lookup"><span data-stu-id="bd851-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd851-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bd851-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="bd851-106">型パラメーターの列挙体をできるように ICorDebugTypeEnum インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bd851-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="bd851-107">型パラメーターの一覧には、(存在する場合)、メソッドの型パラメーターを続けてクラス型パラメーター (存在する場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd851-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd851-108">コメント</span><span class="sxs-lookup"><span data-stu-id="bd851-108">Remarks</span></span>  
 <span data-ttu-id="bd851-109">使用して、 [imetadataimport 2::enumgenericparams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)メソッドを呼び出せば確認クラスの型パラメーターとメソッドの数は、この一覧にパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="bd851-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="bd851-110">型パラメーターは、常に使用できません。</span><span class="sxs-lookup"><span data-stu-id="bd851-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd851-111">要件</span><span class="sxs-lookup"><span data-stu-id="bd851-111">Requirements</span></span>  
 <span data-ttu-id="bd851-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bd851-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd851-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd851-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd851-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd851-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd851-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd851-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
