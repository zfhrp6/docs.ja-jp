---
title: "ICorDebugFrame::GetStackRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1db7617d52e07489ade339b76023e21816835ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="cad64-102">ICorDebugFrame::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="cad64-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="cad64-103">このスタック フレームの絶対アドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="cad64-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad64-104">構文</span><span class="sxs-lookup"><span data-stu-id="cad64-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cad64-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cad64-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="cad64-106">[out]ポインター、`CORDB_ADDRESS`これによって表されるスタック フレームの開始アドレスを指定する`ICorDebugFrame`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cad64-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="cad64-107">[out]ポインター、`CORDB_ADDRESS`これによって表されるスタック フレームの終了アドレスを指定する`ICorDebugFrame`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cad64-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cad64-108">コメント</span><span class="sxs-lookup"><span data-stu-id="cad64-108">Remarks</span></span>  
 <span data-ttu-id="cad64-109">スタックのアドレス範囲は、複数のデバッグ エンジンから収集されインタリーブされたスタック トレースをつなぎ合わせてに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cad64-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="cad64-110">数値の範囲には、スタック フレームのコンテンツに関する情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="cad64-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="cad64-111">スタック フレームの場所の比較に対してのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="cad64-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cad64-112">要件</span><span class="sxs-lookup"><span data-stu-id="cad64-112">Requirements</span></span>  
 <span data-ttu-id="cad64-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cad64-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad64-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cad64-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cad64-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cad64-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cad64-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad64-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
