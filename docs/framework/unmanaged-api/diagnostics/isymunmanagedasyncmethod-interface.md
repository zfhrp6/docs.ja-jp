---
title: "ISymUnmanagedAsyncMethod インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f83723b59f525c06f04b7edeeae953dbf94556
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod インターフェイス
このインターフェイスは、読み取りの補足[ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)です。  
  
## <a name="syntax"></a>構文  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスには、次のメソッドが含まれています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|参照してください[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)です。|  
|[GetAsyncStepInfoCount メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|参照してください[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)です。|  
|[GetCatchHandlerILOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|参照してください[DefineCatchHandlerILOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)です。|  
|[GetKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|参照してください[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)です。|  
|[HasCatchHandlerILOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|参照してください[DefineCatchHandlerILOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)です。|  
|[IsAsyncMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|か、メソッドが非同期の情報を持つかどうかを調べます。<br /><br /> このメソッドが戻る場合`FALSE`し、このインターフェイスで、他のメソッドを呼び出すことはできません。 すべての戻り値は`E_UNEXPECTED`ここでします。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>参照  
 [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
