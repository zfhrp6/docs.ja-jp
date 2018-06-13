---
title: ICorDebugAppDomainEnum Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf8db3b02ba4766d046fc549eec8add31f51069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407921"
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="05b05-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="05b05-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="05b05-103">提供、`Next`メソッドで、指定した数を返します`ICorDebugAppDomainEnum`値の列挙体の次の位置を開始します。</span><span class="sxs-lookup"><span data-stu-id="05b05-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="05b05-104">このインターフェイスは、"ICorDebugEnum"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="05b05-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05b05-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="05b05-105">Methods</span></span>  
  
|<span data-ttu-id="05b05-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="05b05-106">Method</span></span>|<span data-ttu-id="05b05-107">説明</span><span class="sxs-lookup"><span data-stu-id="05b05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05b05-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="05b05-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="05b05-109">コレクションの現在のカーソル位置から指定されたアプリケーション ドメイン数を取得します。</span><span class="sxs-lookup"><span data-stu-id="05b05-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05b05-110">コメント</span><span class="sxs-lookup"><span data-stu-id="05b05-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b05-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="05b05-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b05-112">要件</span><span class="sxs-lookup"><span data-stu-id="05b05-112">Requirements</span></span>  
 <span data-ttu-id="05b05-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="05b05-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b05-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05b05-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05b05-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b05-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b05-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b05-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b05-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="05b05-117">See Also</span></span>  
 [<span data-ttu-id="05b05-118">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05b05-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="05b05-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05b05-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
