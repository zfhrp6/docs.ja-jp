---
title: "ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 866632b3916cd2e35e7832c4d58b5988fa350c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a>ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド
参照してください[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a>戻り値  
 `HRESULT` を返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>参照  
 [ISymUnmanagedAsyncMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
