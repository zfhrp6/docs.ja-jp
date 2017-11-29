---
title: "ICorDebugFunction2::EnumerateNativeCode メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.EnumerateNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2553c8d5e2d2e5b27f56487250c5d3f54c2786d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="f5a0a-102">ICorDebugFunction2::EnumerateNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a0a-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="f5a0a-103">ICorDebugFunction2 オブジェクトによって参照された関数のネイティブ コードのステートメントを含む ICorDebugCodeEnum オブジェクトへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f5a0a-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5a0a-104">`EnumerateNativeCode`.NET Framework の現在のバージョンで実装されていません。</span><span class="sxs-lookup"><span data-stu-id="f5a0a-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a0a-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5a0a-105">Syntax</span></span>  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f5a0a-106">要件</span><span class="sxs-lookup"><span data-stu-id="f5a0a-106">Requirements</span></span>  
 <span data-ttu-id="f5a0a-107">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5a0a-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
