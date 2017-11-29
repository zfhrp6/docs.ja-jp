---
title: "ICorDebugILFrame::GetArgument メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetArgument
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 592354f11faac1fb4d5b050a096f4eab04643c0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="34572-102">ICorDebugILFrame::GetArgument メソッド</span><span class="sxs-lookup"><span data-stu-id="34572-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="34572-103">この Microsoft intermediate language (MSIL) のスタック フレーム内には、指定された引数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="34572-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34572-104">構文</span><span class="sxs-lookup"><span data-stu-id="34572-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34572-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34572-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="34572-106">[in]MSIL のこのスタック フレーム内の引数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="34572-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="34572-107">[out]取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="34572-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34572-108">コメント</span><span class="sxs-lookup"><span data-stu-id="34572-108">Remarks</span></span>  
 <span data-ttu-id="34572-109">`GetArgument` ・ イン タイム (JIT) コンパイル フレームまたは MSIL スタック フレームで、メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="34572-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34572-110">要件</span><span class="sxs-lookup"><span data-stu-id="34572-110">Requirements</span></span>  
 <span data-ttu-id="34572-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="34572-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34572-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34572-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34572-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34572-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34572-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34572-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
