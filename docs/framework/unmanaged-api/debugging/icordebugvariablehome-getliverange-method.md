---
title: "IcorDebugVariableHome::GetLiveRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLiveRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bb86921be3398e6e9653838c1aec6b40ca86469
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetliverange-method"></a>IcorDebugVariableHome::GetLiveRange メソッド
この変数がアクティブ、ネイティブな範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStartOffset`  
 [out]これで、変数が最初ライブ論理オフセット。  
  
 `pEndOffset`  
 [out]直後に、変数はポイント最後ライブ論理オフセット。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
