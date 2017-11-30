---
title: "ICorDebugType2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType2
helpviewer_keywords: ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 658dd1541a1de852c3c001cc7fbb7954f6c7590f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="e93b8-102">ICorDebugType2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e93b8-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="e93b8-103">基本データ型または複合 (ユーザー定義) の型の型の識別子を取得する ICorDebugType インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="e93b8-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e93b8-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e93b8-104">Methods</span></span>  
  
|<span data-ttu-id="e93b8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e93b8-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="e93b8-106">GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="e93b8-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="e93b8-107">取得、 [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)この型にします。</span><span class="sxs-lookup"><span data-stu-id="e93b8-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e93b8-108">コメント</span><span class="sxs-lookup"><span data-stu-id="e93b8-108">Remarks</span></span>  
 <span data-ttu-id="e93b8-109">このインターフェイスは、ICorDebugType インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="e93b8-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e93b8-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e93b8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e93b8-111">例</span><span class="sxs-lookup"><span data-stu-id="e93b8-111">Example</span></span>  
 <span data-ttu-id="e93b8-112">次のコード フラグメントの使用を示しています、 [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e93b8-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="e93b8-113">要件</span><span class="sxs-lookup"><span data-stu-id="e93b8-113">Requirements</span></span>  
 <span data-ttu-id="e93b8-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e93b8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e93b8-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e93b8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e93b8-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e93b8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e93b8-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e93b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93b8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e93b8-118">See Also</span></span>  
 [<span data-ttu-id="e93b8-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e93b8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)