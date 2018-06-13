---
title: ICorDebugAppDomain::EnumerateAssemblies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13137dcf7c2edd96397916cc7db905c9e48a3d0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401601"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="7f283-102">ICorDebugAppDomain::EnumerateAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="7f283-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="7f283-103">アプリケーション ドメイン内のアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="7f283-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f283-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f283-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f283-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f283-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="7f283-106">[out]アプリケーション ドメイン内のアセンブリの列挙子である ICorDebugAssemblyEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7f283-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f283-107">要件</span><span class="sxs-lookup"><span data-stu-id="7f283-107">Requirements</span></span>  
 <span data-ttu-id="7f283-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f283-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f283-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f283-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f283-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f283-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f283-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f283-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
