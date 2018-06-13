---
title: ICorDebugStepper2::SetJMC メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad05d2f6226d570fc854fb48575851dd718e410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418198"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="81475-102">ICorDebugStepper2::SetJMC メソッド</span><span class="sxs-lookup"><span data-stu-id="81475-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="81475-103">アプリケーションの開発者によって作成されたコードでのみこの ICorDebugStepper が手順かどうかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="81475-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="81475-104">このプロセスは、マイ コード (のみ JMC) のデバッグとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="81475-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81475-105">構文</span><span class="sxs-lookup"><span data-stu-id="81475-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81475-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81475-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="81475-107">[in]設定`true`のみ、アプリケーションの開発者によって作成されたためです。 それ以外の場合に設定するコードをステップ実行する`false`です。</span><span class="sxs-lookup"><span data-stu-id="81475-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81475-108">要件</span><span class="sxs-lookup"><span data-stu-id="81475-108">Requirements</span></span>  
 <span data-ttu-id="81475-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="81475-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81475-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81475-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81475-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81475-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81475-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81475-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
