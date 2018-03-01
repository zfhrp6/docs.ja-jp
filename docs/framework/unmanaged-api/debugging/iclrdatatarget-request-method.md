---
title: "ICLRDataTarget::Request メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e7bde3a0bc26a6bc93124fa835c4203cd596906
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request メソッド
実装によって定義されているように、操作を要求する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `reqCode`  
 [in]ユーザー定義になります。  
  
 `inBufferSize`  
 [in]受信要求に使用される入力のバッファーのサイズ。  
  
 `inBuffer`  
 [in]要求を含むバッファー。  
  
 `outBufferSize`  
 [in]応答に使用される出力バッファーのサイズ。  
  
 `outBuffer`  
 [out]応答を格納しているバッファー。  
  
## <a name="remarks"></a>コメント  
 `Request`メソッドには、未指定のカスタム操作の追加が容易になります。 つまり、このメソッドは、インターフェイス定義のリビジョンを行わなくても機能拡張を提供します。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICLRDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
