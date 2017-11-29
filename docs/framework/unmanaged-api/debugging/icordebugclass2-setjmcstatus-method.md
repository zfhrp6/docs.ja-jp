---
title: "ICorDebugClass2::SetJMCStatus メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da9f61bd9a652b4c8e340ddecdee4b48bbdb086e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="98634-102">ICorDebugClass2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="98634-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="98634-103">クラスの各メソッドのメソッドがユーザー定義のコードであるかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="98634-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98634-104">構文</span><span class="sxs-lookup"><span data-stu-id="98634-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98634-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98634-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="98634-106">[in]設定`true`メソッドがユーザー定義であることを示すコードです。 それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="98634-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98634-107">コメント</span><span class="sxs-lookup"><span data-stu-id="98634-107">Remarks</span></span>  
 <span data-ttu-id="98634-108">マイ コード (のみ JMC) ステッパは非ユーザー定義コードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="98634-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="98634-109">ユーザー定義のコードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="98634-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="98634-110">`SetJMCStatus`その他のすべてのメソッドの値が正常に設定する場合でも、任意のメソッドの値を設定が失敗した場合は、S_FALSE の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="98634-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98634-111">要件</span><span class="sxs-lookup"><span data-stu-id="98634-111">Requirements</span></span>  
 <span data-ttu-id="98634-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98634-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98634-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98634-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98634-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98634-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98634-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98634-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
