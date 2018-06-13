---
title: ICorDebugClass2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d234e01e3d47a64b9a001591ee2b61074eea8afb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403395"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="6b6b6-102">ICorDebugClass2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="6b6b6-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="6b6b6-103">クラスの各メソッドのメソッドがユーザー定義のコードであるかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="6b6b6-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b6b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b6b6-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b6b6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b6b6-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="6b6b6-106">[in]設定`true`メソッドがユーザー定義であることを示すコードです。 それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="6b6b6-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b6b6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="6b6b6-107">Remarks</span></span>  
 <span data-ttu-id="6b6b6-108">マイ コード (のみ JMC) ステッパは非ユーザー定義コードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="6b6b6-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="6b6b6-109">ユーザー定義のコードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b6b6-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="6b6b6-110">`SetJMCStatus` その他のすべてのメソッドの値が正常に設定する場合でも、任意のメソッドの値を設定が失敗した場合は、S_FALSE の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="6b6b6-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b6b6-111">要件</span><span class="sxs-lookup"><span data-stu-id="6b6b6-111">Requirements</span></span>  
 <span data-ttu-id="6b6b6-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b6b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b6b6-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b6b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b6b6-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b6b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b6b6-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b6b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
