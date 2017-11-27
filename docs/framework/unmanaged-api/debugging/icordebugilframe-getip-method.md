---
title: "ICorDebugILFrame::GetIP メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f1ea9ad653deeaaa22944517ba5cbdb2f39c6d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="4348b-102">ICorDebugILFrame::GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="4348b-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="4348b-103">命令ポインターの値および命令ポインターの値の取得方法を説明するビットごとの組み合わせの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4348b-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4348b-104">構文</span><span class="sxs-lookup"><span data-stu-id="4348b-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4348b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4348b-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="4348b-106">[out]命令ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="4348b-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="4348b-107">[out]命令ポインターの値が得られた方法を説明する CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4348b-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4348b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4348b-108">Remarks</span></span>  
 <span data-ttu-id="4348b-109">命令ポインターの値は、関数の Microsoft intermediate language (MSIL) コードに、スタック フレームのオフセットです。</span><span class="sxs-lookup"><span data-stu-id="4348b-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="4348b-110">スタック フレームがアクティブな場合は、このアドレスは次の命令を実行するには。</span><span class="sxs-lookup"><span data-stu-id="4348b-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="4348b-111">スタック フレームがアクティブでない場合、このアドレスは、スタック フレームが再アクティブ化したときに実行する次の命令をします。</span><span class="sxs-lookup"><span data-stu-id="4348b-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="4348b-112">このフレームが・ イン タイム (JIT) コンパイルされたフレームの場合は、命令ポインターの値が値が概数のみであるために、実際のネイティブ命令ポインターから逆方向にマップすることによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="4348b-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4348b-113">要件</span><span class="sxs-lookup"><span data-stu-id="4348b-113">Requirements</span></span>  
 <span data-ttu-id="4348b-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4348b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4348b-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4348b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4348b-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4348b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4348b-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4348b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
