---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド
IL オフセットの非同期メソッドをラップするコンパイラで生成された catch ハンドラーを設定します。  
  
 デバッガーは生成された catch の IL オフセットを使用してが非ユーザー コードで場合でも、ユーザー コード メソッドで発生する可能性があるかのように catch を処理します。 具体的への応答で使用されている、 **CatchHandlerFound**例外イベント。  
  
## <a name="syntax"></a>構文  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>戻り値  
 `HRESULT` を返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>参照  
 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
