---
title: "ICorDebugProcess2::GetVersion メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetVersion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84db785d47f97fe058b8a66070bcf4757fa11517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="7d68e-102">ICorDebugProcess2::GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="7d68e-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="7d68e-103">このプロセスで実行されている共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d68e-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d68e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d68e-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d68e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d68e-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="7d68e-106">[out]ランタイムのバージョン番号を格納する COR_VERSION 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7d68e-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d68e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7d68e-107">Remarks</span></span>  
 <span data-ttu-id="7d68e-108">`GetVersion`プロセスのランタイムが読み込まれていない場合、メソッドはエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="7d68e-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d68e-109">要件</span><span class="sxs-lookup"><span data-stu-id="7d68e-109">Requirements</span></span>  
 <span data-ttu-id="7d68e-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d68e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d68e-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d68e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d68e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d68e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d68e-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d68e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
